# 내비게이션 요소, 스크립트 연결

### 내비게이션 요소

subview와 subcatalog는 jamkit 화면이 실행되면 처음으로 구성되는 내비게이션 요소입니다.

그동안 다른 jamkit의 요소 중에 데이터가 포함된 요소는 showcase, banner, panes, collection 등이 있습니다. 그중에서 우리는 showcase와 panes를 배웠습니다.

collection은 일반적인 데이터를 다룹니다. 특정한 object에 묶이지 않고, 데이터를 관리할 수 있습니다. 구조는 showcase와 동일하며, showcase나 banner 등에서 collection의 데이터를 이용할 수 있습니다.

`=object showcase: name={name}@collection`

banner는 데이터가 슬라이드되는 object로서, transition 효과를 다양하게 줄 수 있습니다.

### subcatalog

jamkit은 기본적으로 catalog로 화면이 구성되는데, 앱의 메뉴나 사이드바 등 앱의 각 영역을 그룹화할 수 있습니다. 즉, 앱의 각 부분이나 화면을 subcatalog 단위로 나눠서 구성한다고 보면 됩니다. 그래서 앱을 설계할 때, subcatalog 단위로 잘 나눠야 합니다.

카탈로그 엑셀 문서에 subcatalogs라는 시트가 있고, 각 subcatalog는 소문자로 된 id가 부여되어 있습니다.

<figure><img src="../.gitbook/assets/subcatalog sample.png" alt=""><figcaption></figcaption></figure>

#### subcatalog 액션

`action=subcatalog, subcatalog={name}, target=self/popup`

위 명령어를 쓰면 catalog\_{name}이 현재 화면 내에서 바뀌거나 팝업으로 뿌려집니다. 다만, 위 명령어는 거의 쓰지 않고 subview를 불러서 subcatalog를 띄우는 방식으로 씁니다.

정리하면, 앱은 catalog라는 기본 화면 내에 subcatalog가 있고, 내비게이션으로 보면 subcatalog 위에서 page, popup, bottom-sheet 등이 뜨는 것입니다.

#### controller, module 속성

controller는 필요한 기능을 추가적으로 부여하는 속성으로, 예를 들면 사용자 설정을 다룰 때는 SettingView라는 controller를 쓸 수 있습니다.

module은 sbml/sbss 파일이 많아질 경우, 폴더로 묶을 수 있는 속성입니다.

### subview

위에서도 얘기했듯이 jamkit에서는 subcatalog를 직접 다루는 일은 거의 없고 subview라는 논리적인 개념으로 연결하여 이용합니다. subview는 subcatalog만 앱에 올릴 수 있습니다. 하나의 subcatalog는 여러 subview와 연결될 수 있으나, 대부분 1 대 1로 연결됩니다.

카탈로그 엑셀 문서에 subview라는 시트가 있고, 각 subview는 "V\_"로 시작하는 대문자로 된 id가 부여되어 있습니다. subview는 앱에서 동적으로 추가할 수 없습니다.

<figure><img src="../.gitbook/assets/subview sample.png" alt=""><figcaption></figcaption></figure>

앱이 처음 실행되면 catalog\_main.sbml이 실행됩니다. 내부에는 id가 container인 blank object가 들어 있습니다. 참고로, catalog\_main의 subview 이름은 "\_\_MAIN\_\_"으로 고정입니다.

catalog\_main은 catalog.bon에 있는 default-subview를 찾아서 해당 subview와 연결된 subcatalog를 화면에 띄웁니다.

```javascript
// catalog_main.sbml
=begin catalog
=object blank: id=container, style=blank_container
=end catalog

// catalog.bon
{
    "title": "MainApp 카탈로그",
    "version": "1.0",
    "uses-database": "yes",
    "database-version": "2.0",
    "default-subview": "V_HOME",
    "orientations": "portrait,landscape"
}
```

`action=subview, subview={name}, target=embed/self/popup`

위 명령어를 쓰면 해당 subview에 연결된 subcatalog가 container 내에 뜨거나 전체화면 팝업으로 뜹니다.

* target=embed (default)\
  catalog\_main에 뜬 container 영역 위에 겹쳐셔 보임(전체화면 아닐 수 있음)
* target=self\
  catalog\_main에 뜬 container 영역을 대체하면서 보임(전체화면 아닐 수 있음)
* target=popup\
  catalog\_main 위에 전체화면으로 보임

### 스크립트 연결

#### controller

현재의 subview에 연결된 js 파일에서 controller 객체를 통해 스크립트를 활용할 수 있습니다.

아래는 버튼을 누르면 start라는 스크립트를 실행하도록 만든 것입니다.

```javascript
// catalog_start.sbml
=begin catalog: script-when-loaded=on_loaded

=begin title
=object image: filename=img_title.png, style=img_title
=end title

=object showcase: name=onboarding, style=showcase_onboarding

=begin buttons
=object button: script=start, label="@{Getting Started}", style=btn_action
=end buttons

=end catalog


// catalog_start.js
function start() {
    controller.action("bottom-sheet", {
        "display-unit": "S_START_WALLET"
    });
}

function create_wallet() {
    controller.action("subview", {
        "subview":"V_WALLET.CREATE",
        "target":"popup"
    });
    controller.action("bottom-sheet-close");
}

function restore_wallet() {
    controller.action("bottom-sheet-close");
    controller.action("subview", {
        "subview":"V_WALLET.RESTORE",
        "target":"popup"
    });
}
```

#### view

sbml과 sbss가 구현되는 화면 자체를 모두 view라고 부릅니다. view를 통해서 그 안에 들어있는 오브젝트에서 instance를 얻거나 명령을 내릴 때 씁니다.

#### object

object는 controller나 view로부터 얻어내야 합니다.

`var obj = veiw.object(id)`라고 하면 그 object의 instance가 obj라는 함수로 넘어옵니다. 그때부터는 object에 액션을 주거나 프로퍼티나 밸류를 변경할 수 있습니다.

#### controller, view, object의 관계

화면 전체를 관장하는 controller가 있고, 화면 내에는 여러 개의 view가 있을 수 있습니다. 그 view 안에 object가 들어갑니다. 각 view에서 접근해서 데이터를 얻거나 동작을 실행할 수 있습니다.

#### owner

owner는 container 오브젝트를 포함한 원본 view를 가리킵니다.

예를 들여, showcase 오브젝트에 header가 있다면, showcase 오브젝트를 품은 sbml이 있고, header를 구현하는 sbml이 있을 것입니다.

이때, showcase\_{name}\_header.sbml에는 owner가 생기며, 이 owner는 showcase 오브젝트를 품은 showcase\_{name}\_header.sbml view를 가리킵니다.

특정 view가 자기 바깥의 view에서 object를 찾으려면 `controller.object(id)`로 찾습니다.

#### host

host는 popup과 bottom-sheet를 띄운 원본 view를 가리킵니다.
