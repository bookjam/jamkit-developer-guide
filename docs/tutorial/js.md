# JS 통신, 데이터 바인딩

### Jamkit에서의 컨텍스트란?

웹과 Jamkit이 크게 다른 점 중 하나가 컨텍스트입니다. 웹은 하나의 컨텍스트로 되어 있어서 JavaScript 함수를 한번 정의하면 어디서든 불러서 활용할 수 있습니다.

Jamkit은 컨텍스트가 분리되어 있어서 특정 화면에 연결된 JS 파일에 정의된 함수만 불러올 수 있으며 화면이 살아있는 동안에만 동작합니다.

다만, 예외적으로 화면이 있더라도 js 파일이 없는 경우는 sbmls 오브젝트, sbml 오브젝트, section 오브젝트뿐입니다. 이 오브젝트에서 js를 활용하려면 해당 오브젝트가 포함된 sbml에 연결된 js 파일에 정의해야 합니다. 예를 들면, catalog\_home.sbml에 구현된 sbml 오브젝트에서 스크립트를 실행하면 Jamkit은 해당 스크립트를 catalog\_home.js에서 찾습니다.

정리하면, Jamki에서는 변수나 함수 등이 js 파일 안에서 독립적으로 정의되고 실행된다는 것입니다. 별개의 함수를 동시에 실행할 수 있는 멀티스레딩의 장점이 있습니다.

하나의 컨텍스트에서는 순차적으로 실행됩니다. 아래와 같은 구성에서는 on\_loaded 함수가 먼저 실행되고 끝나야, 이후 abc 함수가 실행됩니다. 이때 처음 실행되는 함수가 loop된다면 다음 함수는 실행되지 않습니다.

```javascript
// sbml 파일
=begin cell: script-when-loaded=on_loaded
=object button: script=abc
=end cell

// js 파일
function on_loaded() {
...
}

function abc() {
...
}
```

### 멀티 컨텍스트 간의 통신

지금부터 컨텍스트 간에 통신하는 방법을 설명합니다.

catalog\_home에서 popup을 띄워 데이터를 주고 받는다고 할 때, 해당 popup sbml에서 처리해도 되지만 화면이 닫히면 데이터 통신에 실패하기 때문에 앱이 실행되는 동안 항상 살아있는 catalog\_main에서 함수를 처리합니다.

```javascript
// S_USER_popup.sbml
=object button: script=report_abuser
```

{% code overflow="wrap" %}
```javascript
subview가 "__MAIN__"인 catalog_main에 연결된 report_abuser를 실행하고, 거기서 보내준 데이터를 다시 받아서 on_report_abuser를 실행함

// S_USER_popup.js
function report_abuser() {
    controller.action("script", {
        "script": "report_abuser",
        "subview": "__MAIN__",
        "return-context": $evn["CONTEXT"]
        "return-script": "on_report_abuser"
    });
}

function on_report_abuser() {
...
}
```
{% endcode %}

{% code overflow="wrap" %}
```javascript
return-context에서 온 데이터를 받아서 처리하고 그 결과값을 return-context로 넘기고 return-script를 실행함

// catalog_main.js
function report_abuser() {
...

    controller.action("script", {
        "script": params["return-script"],
        "context": params["return-context"]
}
```
{% endcode %}

#### actions-helper

위 내용은 로우 레벨로 설명한 내용이며, 실제로는 actions-helper라는 모듈을 사용합니다. Scripts 폴더에 해당 모듈을 넣어야 합니다.

{% code overflow="wrap" %}
```javascript
// S_USER_popup.js
const actions = require("actions-helper")

function report_abuser() {
    actions.invoke("__MAIN__", "report_abuser", {
        ...
    })
        .then(function(result) {
            ...
        });
}
```
{% endcode %}

{% code overflow="wrap" %}
```javascript
// catalog_main.js
const actions = require("actions-helper")

function report_abuser(params) {
    actions.resolve(params, {
        ...
    });
    actions.reject(params, {
        ...
    });
}
```
{% endcode %}

멀티컨텍스트 간에 오가는 데이터는 string 형태로서, JSON.stringfy하여 넘겨줘야 합니다.

#### routes-to-topmost 속성

특정 view, 예를 들어 catalog\_home에 popup, page, bottom-sheet가 뜬 상황에서 catalog\_home에 데이터를 전달하거나 함수를 실행하고 싶을 때, 이 데이터가 catalog\_home에 전달되지 않거나 catalog\_home.js가 호출되지 않고, 최상단에 뜬 화면(popup, page, bottom-sheet)로 전달되는 경우가 있습니다. 이럴 때는 rotues-to-topmost=no 속성을 주어야 합니다.

{% code overflow="wrap" %}
```javascript
// S_USER_popup.js
const actions = require("actions-helper")

function report_abuser() {
    actions.invoke("__MAIN__", "report_abuser", {
        "routes-to-topmost": "no"
    })
        .then(function(result) {
            ...
        });
}
```
{% endcode %}

#### host, owner 오브젝트

host 오브젝트는 popup이나 bottom-sheet가 뜬 상태에서, 그 popup이나 bottom-sheet를 띄운 view를 가리킵니다. view를 따로 지정하지 않더라도 해당 view의 js 파일에서 스크립트를 실행할 수 있습니다.

{% code overflow="wrap" %}
```javascript
// S_USER_popup.js
host.action("script", {
    ...
})
```
{% endcode %}

owner 오브젝트는 컨테이너 오브젝트가 속한 view를 가리킵니다. 예를 들어, catalog\_main에 cell 오브젝트가 있다면 cell의 js 파일에서 owner를 지정하면 cell을 포함한 catalog\_main.js에서 스크립트를 찾습니다.

{% code overflow="wrap" %}
```javascript
// cell.js
owner.action("script", {
    ...
})
```
{% endcode %}

### 데이터 바인딩

#### 데이터 공유 오브젝트

컨텍스트는 분리되어 있지만, 모든 컨텍스트가 데이터를 공유하는 오브젝트가 있습니다. js 파일 내에서 document, storage, keychain입니다.

이 오브젝트들은 key, value로 데이터를 입력하고 가져옵니다. 예를 들어, 아래처럼 입력하면 어떤 js 파일에서든 id를 통해 value를 가져올 수 있습니다.

document는 앱이 실행 중에만 메모리가 데이터가 남아 있으며, storage는 앱이 종료되어도 데이터가 저장됩니다.

```
// js 파일
document.value("username", "me")
keycahin.password(" ", " ")

// 다른 js 파일
document.value("username")
```

#### 데이터 바인딩(변경된 데이터 전파)

어떤 특정한 데이터가 변경되었을 때, 여러 화면에서 해당 데이터를 변경해야 하는 경우가 있습니다. 하지만 현재 어떤 화면이 떠 있는지 알 수 없기 때문에 관련 파일에 전부 전파해줘야 합니다.

파일 구조는 아래와 같습니다. 변경된 데이터를 전파하는 것은 주로 catalog\_main입니다.

{% code overflow="wrap" %}
```javascript
// sbml: 변경된 데이터를 받으려고 하는 파일
=begin cell: data-binding="xx2, {id}, ...", \
             script-when-data-changed=on_data_changed

// js
function on_data_changed(xx2, data) {
    ...
}

// catalog_main.js
controller.update("xx2" , {
    ...
});
```
{% endcode %}
