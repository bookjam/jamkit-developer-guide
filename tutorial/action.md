# 액션과 이벤트, 스크립트, 화면 전환

### action 처리

jamkit에는 action과 event가 있는데, event를 받아서 action을 처리하는 방법입니다.

action과 script는 동일한 레벨에서 동작합니다. action이라는 단어를 script라는 단어로 바꾸면 해당 script가 실행되는 구조라고 생각하면 됩니다.

action은 반드시 특정한 event가 발생해야 실행됩니다. 주로 object마다 발생할 수 있는 event가 정의되고, 그 event에 따른 action을 property로 넣어서 실행합니다.

#### button의 action

<table><thead><tr><th width="97">action</th><th>description</th><th>parameter</th></tr></thead><tbody><tr><td>toast</td><td>하단에 검은색 텍스트가 잠깐 떴다 사라짐</td><td>message</td></tr><tr><td>alert</td><td>얼럿창이 떠서 '확인'을 누를 때까지 유지됨</td><td>message</td></tr></tbody></table>

```javascript
// sbml
=object button: action="toast", \
                params="message=\"hello\""
    
=object button: action="toast", \
                message="hello"
```

#### event의 종류

대부분의 event는 object의 생애주기에 따라서 발생합니다. label이나 image 등의 정적인 object에는 event가 없습니다.

사용자 지정 event는 없으며, 필요한 경우 사용자 지정 script를 만들면 됩니다.

#### showcase의 action

showcase나 youtube 등 대부분의 object에서는 다양한 event가 발생합니다. 주로 action-when-{event}, params-when-{event}라는 코드를 씁니다.

seletable=yes가 설정된 showcase의 cell을 탭하면 'selected'라는 event가 발생하고 그에 따른 action이 발생합니다.

이때, 해당 cell의 데이터가 자동으로 parameter화하여 전달합니다. prameter로 쓸 데이터를 미리 해당 showcase 데이터에 key와 value로 저장해두어야 합니다.

{% code overflow="wrap" %}
```javascript
// cell을 누를 때, 해당 cell의 title을 toast로 띄움
#showcase_list: width=1pw, height=0.9ph, \
               keep-count=6, preload-count=6, column-count=1, \
                cell-size="0.9pw 50dp", cell-spacing=10dp, \
                selectable=yes, \
                action-when-selected="toast", \
                params-when-selected="message=\"hi {title}\""
```
{% endcode %}

{% code overflow="wrap" %}
```javascript
// cell을 누를 때, 해당 cell에 설정된 url을 웹브라우로 띄움
#showcase_list: width=1pw, height=0.9ph, \
               keep-count=6, preload-count=6, column-count=1, \
                cell-size="0.9pw 50dp", cell-spacing=10dp, \
                selectable=yes, \
                action-when-selected="link", \
                params-when-selected="url="
```
{% endcode %}

### 스크립트 실행

action은 스크립트를 모르더라도 필요한 기능을 구현하기 위한 것으로, 실제로는 대부분 스크립트를 많이 사용합니다.

스크립트는 위에서 봤던 코드에서 action이라는 단어 대신 script를 쓰면 됩니다. params는 없으며, 대신 연계된 js 파일에서 해당되는 함수를 불러옵니다.

{% code overflow="wrap" %}
```javascript
button에서 script 실행

// sbml
=object button: script="alert_message"

// js
funtion alert_message(params) {
    console.log("alert_message");
    console.log(JSON.stringify(params, null, 2);
}
```
{% endcode %}

```javascript
showcase에서 script 실행

// sbml
#showcase_list: width=1pw, height=0.9ph, \
               keep-count=6, preload-count=6, column-count=1, \
                cell-size="0.9pw 50dp", cell-spacing=10dp, \
                selectable=yes, \
                script-when-selected="showcase_seleted", \
                params-when-selected=""

// js
funtion showcase_seleted(params) {
    console.log(JSON.stringify(params, null, 2);
}
```

#### jamkit에서 action을 실행하는 3가지 주체

jamkit에서는 action을 실행하는 3가지 주체로는 controller, view, object가 있습니다.

* controller 예시

```javascript
// js
controller.action("toast", {
    "message" : "hi"
});
```

### 화면 전환

가장 상위의 catalog 화면 위에서 구현 가능한 화면 전환은 page, popup, bottom sheet가 있습니다.

* page: 우측에서 들어와서 현재 화면 전체를 덮는 화면
* popup: fade-in 되어 현재 화면 중앙을 차지하는 화면
* bottom-sheet: 화면 하단에서 튀어나오는 화면

#### 파일 이름 규칙

{% hint style="info" %}
* **display-unit - 특정 display-unit를 지정하는 경우(has-own-sbml=yes로 설정되어야 함)**\
  display-unit : S\_MY\_123\
  <mark style="color:red;">S\_MY\_123</mark>\_bottom\_sheet.sbml/sbss를 찾는다
* **template - 템플릿을 지정하는 경우**\
  name: apps\
  template: installed\
  showcase\_<mark style="color:red;">apps</mark>\_<mark style="color:red;">installed</mark>\_bottom\_sheet.sbml/sbss를 찾는다
* **name - 쇼케이스 이름을 지정하는 경우**\
  name: apps\
  showcase\_<mark style="color:red;">apps</mark>\_bottom\_sheet.sbml/sbss를 찾는다
* **defaut - 아무것도 지정하지 않은 경우**\
  showcase\_<mark style="color:red;">default</mark>\_bottom\_sheet.sbml/sbss를 찾는다
{% endhint %}

```
// sbml
=object button: action="bottom-sheet", display-unit="S_123"
```

#### Bottom Sheet

bottom sheet의 높이는 해당 sbml에 입력된 내용에 따라 결정됩니다. 화면 전체 높이보다 내용이 많을 경우에는 bottom sheet에 지정한 height만큼 올라오고 한번 더 swipe up해야 전체 화면으로 덮입니다.

sbml에서 section을 display=block으로 처리하거나 object를 넣으면 해당 영역만큼 올라옵니다. height를 지정하지 않으면 아주 살짝 올라옵니다.

bottom sheet의 상단 handle의 모양과 크기는 직접 구현해야 합니다.

#### Page

page는 화면 상단에 navibar 영역이 자동으로 적용됩니다. 해당하는 파일은 subview\_navibar.sbml/sbss인데요, 요즘은 거의 사용하지 않고, navibar를 직접 구현합니다.

그래서 page에서는 hides-navibar=yes 속성으로 nivibar를 숨기고, has-own-navibar=yes 속성으로 직접 만든 navibar을 적용합니다. 이 데이터는 엑셀이나 구글 시트의 해당 display-unit에 key, value로 설정합니다.

page는 겹칠 수 있습니다. 만약, 겹치지 않고 해당 page에 덮어쓰게 만들고 싶다면 target=self 속성을 주면 됩니다.

#### Popup

popup은 크기를 조절할 수 없습니다. 그래서 크기를 조절하려면 page-background-color를 투명하게 주고, 가운데 object를 원하는 크기로 넣어서 처리합니다.

### showcase와 연결하기

cell을 탭할 때, 특정한 내용을 page, popup, bottom sheet로 띄울 수 있습니다.

```javascript
// sbml
=object showcase: name=apps, selectable=yes, \
                action-when-seleted=page, \
                
```
