# 컨테이너 오브젝트

!!! note

    구글 스프레드시트는 [**여기**](https://docs.google.com/spreadsheets/d/1439AhKBU1wfHTo7vbrq6Q8l87SCih8xpCNptIMtygxs/edit?usp=sharing)에서 확인하세요.

### 페인(Panes) 오브젝트 <a href="#panes" id="panes"></a>

페인(Panes) 오브젝트는 pane이라 부르는 페이지를 여러 개 포함할 수 있는 콘테이너 오브젝트이다. 각 pane의 크기는 오브젝트의 크기와 동일하며, pane의 내용은 sbml로 표현한다. pane 간의 이동은 가로 스크롤이나 네비게이션 바를 이용한다. 네비게이션 바는 오브젝트 상단이나 하단, 혹은 좌우에 배치할 수 있으며, 네비게이션 바에는 각 pane마다 대응되는 셀(cell)이 있어서 해당 셀을 선택하면 이와 대응되는 pane이 화면에 나타난다. 네비게이션의 셀의 내용은 sbml로 표현한다. 페인 오브젝트는 헤더(header)와 툴바(toolbar)를 포함할 수 있으며 각각의 내용은 sbml로 표현한다.

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_1" id="_1"></a>

```
=object panes: name="main", has-navibar=yes, navibar-cell-size="0.2pw, 2em"
```

#### 속성 <a href="#_2" id="_2"></a>

| 속성                       | 타입(허용값)                     | 기본값       | 단위                  | 설명                                                                                           |
| ------------------------ | --------------------------- | --------- | ------------------- | -------------------------------------------------------------------------------------------- |
| name                     | String                      | None      |                     | 데이터의 이름. 로컬 데이터베이스의 panes 테이블에서 panes의 이름이 name인 항목을 가리킨다.                                   |
| filename                 | 파일명                         | None      |                     | 데이터가 저장된 파일명. 파일의 포맷은 json 이어야 하며, 파일은 Texts 디렉토리에 들어있어야 한다.                                 |
| alternate-name           | String                      | None      |                     | sbml 파일을 선택할 때 사용할 가상의 이름.                                                                   |
| catalog                  | String                      | None      |                     | 데이터가 포함되어 있는 카탈로그의 ID.                                                                       |
| subcatalog               | String                      | None      |                     | 특정 카테고리가 포함되어 있는 서브카탈로그의 값. category의 값과 함께 사용된다.                                            |
| category                 | String                      | None      |                     | 데이터에서 특정 카테고리만을 선택할 때 지정함.                                                                   |
| number-of-panes          | Integer                     | 0         |                     | pane의 갯수. name으로 데이터를 지정하지 않을 때 사용함.                                                         |
| pane-display-unit        | String                      | None      |                     | name으로 데이터를 지정하지 않을 때 사용할 데이터의 displayUnit 항목.                                               |
| focused-pane             | String 혹은 Integer           | None      |                     | 로드 시에 선택할 pane의 항목. displayUnit 값이나 pane의 index 값을 지정할 수 있다.                                 |
| has-header               | Boolean                     | no        |                     | 헤더를 포함하려면 yes를 지정함.                                                                          |
| header-display-unit      | String                      | None      |                     | 헤더에 사용할 데이터의 displayUnit 항목.                                                                 |
| header-width             | Float                       | 0         | dp, em, layout의 상대값 | 헤더의 너비. 0이면 자동계산.                                                                            |
| header-height            | Float                       | 0         | dp, em, layout의 상대값 | 헤더의 높이. 0이면 자동계산.                                                                            |
| has-toolbar              | Boolean                     | no        |                     | 툴바를 포함하려면 yes를 지정함.                                                                          |
| toolbar-display-unit     | String                      | None      |                     | 툴바에 사용할 데이터의 displayUnit 항목.                                                                 |
| toolbar-height           | Float                       | 0         | dp, em, layout의 상대값 | 툴바의 높이. 0이면 자동계산.                                                                            |
| toolbar-position         | top / bottom                | bottom    |                     | 툴바의 위치.                                                                                      |
| has-navibar              | Boolean                     | no        |                     | 네비게이션 바를 포함하려면 yes를 지정함.                                                                     |
| navibar-cell-size        | Size                        | "0, 0"    | dp, em, layout의 상대값 | 네비게이션 바의 셀 크기.                                                                               |
| navibar-cell-spacing     | Float                       | 0         | dp, em, layout의 상대값 | 네비게이션 바의 셀 간격.                                                                               |
| navibar-margin           | Side                        | "0 0 0 0" | dp, em, layout의 상대값 | 네비게이션 바의 상하좌우 여백. 축약형 사용 가능. 예) "1em", "1em 20dp", "1em 1.5em 0 1.2em"                       |
| navibar-position         | top / bottom / left / right | top       |                     | 네비게이션 바의 위치.                                                                                 |
| navibar-center-align     | Boolean                     | no        |                     | 네비게이션 바 내의 셀들을 가운데로 정렬 하려면 yes를 지정함. 이 때, 선택되어 있는 셀을 기준으로 가운데 정렬을 한다.                        |
| navibar-background-color | Color                       | 투명        |                     | 네비게이션 바의 배경색.                                                                                |
| single-mode              | Boolean                     | no        |                     | pane 영역이 싱글 모드로 동작하려면 yes를 지정함. 싱글 모드로 동작하면 스크롤을 통한 pane 간의 이동이 불가하며, 네비게이션 바를 통해 이동을 해야 한다. |
| weekday-mode             | Boolean                     | no        |                     | pane 데이터가 요일별 구성으로 동작하려면 yes를 지정함. 요일별 구성을 적용하면 로드 시에 당일 요일에 해당하는 pane이 자동으로 선택된다.           |
| monday-is-first          | Boolean                     | no        |                     | 요일별 pane 데이터가 월요일부터 시작하려면 yes를 지정함. "no"를 지정하면 일요일부터 시작한다.                                   |
| weekday-offset           | Integer                     | 0         |                     | 요일의 pane 데이터가 시작되는 네비게이션 상의 위치를 지정함. 1로 지정하면 두번째 pane 부터 차례대로 요일을 부여한다.                      |
| shows-throbber           | Boolean                     | no        |                     | 네비게이션을 통한 pane 간의 이동 시에 throbber를 보여주려면 yes를 지정함.                                            |
| bounces                  | Boolean                     | yes       |                     | pane 영역의 바운스 효과를 없애려면 no를 지정한다.                                                              |

#### 액션 <a href="#_3" id="_3"></a>

| 액션     | 매개변수 | 설명             |
| ------ | ---- | -------------- |
| reload |      | 오브젝트를 다시 로드한다. |

#### 이벤트 <a href="#_4" id="_4"></a>

#### 선택된 셀의 표현 방법 <a href="#_5" id="_5"></a>

내비게이션 바에서 현재 선택된 셀을 위한 sbml을 로딩할 때 선택된 상태를 나타내는 환경변수를 sbss에서 사용할 수 있다. 환경변수 이름은 $STATE이고 선택된 셀에는 $STATE의 값으로 "selected"가 지정된다. 따라서 아래와 같은 방법으로 sbss를 작성하면 선택된 셀에 특정 색상 값이나 이미지 등을 지정할 수 있다.

```javascript
if $STATE == "selected"
    /cell: text-color=#f00
else
    /cell: text-color=#000
end
```

#### 디바이스별 고려사항 <a href="#_6" id="_6"></a>

메모리가 부족한 디바이스 등에서 적은 리소스로 동작을 시키려면 싱글 모드를 사용해야 한다.

### 배너(Banner) 오브젝트 <a href="#banner" id="banner"></a>

배너(Banner) 오브젝트란 한 개 이상의 배너 페이지를 자동으로 롤링하여 보여주는 콘테이너 오브젝트이다. 배너 오브젝트는 주로 화면 상단에 배치되어 광고용으로 사용된다. 배너 오브젝트에 포함된 배너 페이지를 셀(cell)이라고 하며, 각 셀의 내용은 sbml을 이용하여 표현한다. 여러 개의 셀이 자동으로 전환될 때의 시간 간격이나 효과 등을 지정할 수 있다.

#### 사용예 <a href="#_7" id="_7"></a>

```
=object banner: name="main", rotate-interval=1.0
```

#### 속성 <a href="#_8" id="_8"></a>

| 속성                    | 타입(허용값)                                                                                  | 기본값       | 단위                  | 설명                                                                     |
| --------------------- | ---------------------------------------------------------------------------------------- | --------- | ------------------- | ---------------------------------------------------------------------- |
| name                  | String                                                                                   | None      |                     | 데이터의 이름. 로컬 데이터베이스의 banners 테이블에서 banner의 이름이 name인 항목을 가리킨다.          |
| filename              | 파일명                                                                                      | None      |                     | 데이터가 저장된 파일명. 파일의 포맷은 json 이어야 하며, 파일은 Texts 디렉토리에 들어있어야 한다.           |
| alternate-name        | String                                                                                   | None      |                     | sbml 파일을 선택할 때 사용할 가상의 이름.                                             |
| catalog               | String                                                                                   | None      |                     | 데이터가 포함되어 있는 카탈로그의 ID.                                                 |
| subcatalog            | String                                                                                   | None      |                     | 특정 카테고리가 포함되어 있는 서브카탈로그의 값. category의 값과 함께 사용된다.                      |
| category              | String                                                                                   | None      |                     | 데이터에서 특정 카테고리만을 선택할 때 지정함.                                             |
| data-downloadable     | Boolean                                                                                  | no        |                     | 데이터를 외부에서 다운로드하려면 yes를 지정한다.                                           |
| data-url              | URL                                                                                      | None      |                     | 데이터를 다운로드 받을 URL. 이 때 다운로드되는 데이터의 형식은 json이어야 한다.                      |
| data-path             | String                                                                                   | None      |                     | 다운로드한 데이터 중 셀이 사용할 데이터의 루트를 지정한다.                                      |
| data-key              | String                                                                                   | None      |                     | 다운로드한 데이터에서 id로 사용할 항목을 지정한다.                                          |
| transition-style      | slide / dissolve / cross-dissolve / none                                                 | slide     |                     | 배너의 트랜지션 효과.                                                           |
| rotate-interval       | Float                                                                                    | 7         |                     | 배너의 트랜지션 간격. 초단위로 지정한다.                                                |
| transition-duration   | Float                                                                                    | 0.3       |                     | 트랜지션의 애니메이션 시간. 초단위로 지정한다.                                             |
| has-page-control      | Boolean                                                                                  | no        |                     | 페이지 컨트롤을 포함하려면 yes를 지정함.                                               |
| page-control-height   | Float                                                                                    | 0         | dp, em, layout의 상대값 | 툴바의 높이. 0이면 자동계산.                                                      |
| page-control-position | left-top / left-bottom / right-top / right-bottom / top / right / bottom / left / center | bottom    |                     | 페이지 컨트롤의 위치.                                                           |
| page-control-margin   | Side                                                                                     | "0 0 0 0" | dp, em, layout의 상대값 | 페이지 콘트롤의 상하좌우 여백. 축약형 사용 가능. 예) "1em", "1em 20dp", "1em 1.5em 0 1.2em" |
| inner-page-control    | Boolean                                                                                  | no        |                     | 페이지 컨트롤을 쇼케이스 오브젝트 내로 배치하려면 yes를 지정한다.                                 |
| page-dot-size         | Size                                                                                     | "0, 0"    | dp, em, layout의 상대값 | 페이지 점 이미지의 크기. "0, 0"이면 자동계산한다.                                        |
| page-dot-spacing      | Float                                                                                    | 0         | dp, em, layout의 상대값 | 페이지 점 사이의 간격.                                                          |
| active-page-dot       | 파일명                                                                                      | None      |                     | 활성화된 페이지 점 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                        |
| inactive-page-dot     | 파일명                                                                                      | None      |                     | 비활성화된 페이지 점 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                       |

#### 액션 <a href="#_9" id="_9"></a>

| 액션     | 매개변수 | 설명             |
| ------ | ---- | -------------- |
| reload |      | 오브젝트를 다시 로드한다. |

#### 이벤트 <a href="#_10" id="_10"></a>

N/A

#### 외부 데이터를 사용하는 방법 <a href="#_11" id="_11"></a>

배너 오브젝트는 외부 데이터를 사용하여 셀의 내용을 채워넣는 기능을 지원한다. 외부 데이터는 웹(HTTP/S)을 통해 액세스 가능해야 하며, 요청에 대한 응답으로 json으로 표현된 데이터를 전송해야 한다. 웹 요청은 GET 메소드를 사용하며, 해당 배너의 모든 데이터를 한번에 포함하여 응답해야 한다. 배너 오브젝트에서 외부 데이터를 사용하려면 data-downloadable을 yes로 지정하고, data-url 속성에 외부 데이터의 URL을 지정하면 된다.

```javascript
=object banner: name="ads", data-downloadable=yes, \
                data-url="http://www.munhak.com/ads"
```

### 쇼케이스(Showcase) 오브젝트 <a href="#showcase" id="showcase"></a>

쇼케이스(Showcase) 오브젝트란 말그대로 진열장이다. 쇼케이스 오브젝트를 이용하여 여러 개의 상품이나 컨텐츠들을 늘어놓고 진열할 수 있다. 쇼케이스 오브젝트는 격자형 모양으로 상품들을 진열하는 데, 격자의 한 칸을 가리켜 셀(cell)이라고 하며, 각 셀은 sbml을 이용하여 표현한다. 쇼케이스 오브젝트는 고정 크기이거나 가로/세로 스크롤이 가능하도록 지정할 수 있다. 쇼케이스 오브젝트 내에 포함된 셀들은 정렬이 가능하며, 정렬의 기준은 sortkey와 sortorder 속성을 이용하여 변경할 수 있다. 쇼케이스 오브젝트는 헤더(header)와 푸터(footer), 툴바(toolbar)를 포함할 수 있는데, 이들의 내용은 각각 sbml로 표현한다.

#### 사용예 <a href="#_12" id="_12"></a>

```
=object showcase: name="magazine"
```

#### 속성 <a href="#_13" id="_13"></a>

| 속성                      | 타입(허용값)                                                                                  | 기본값                         | 단위                  | 설명                                                                                                                 |
| ----------------------- | ---------------------------------------------------------------------------------------- | --------------------------- | ------------------- | ------------------------------------------------------------------------------------------------------------------ |
| name                    | String                                                                                   | None                        |                     | 데이터의 이름. 로컬 데이터베이스의 showcases 테이블에서 showcase의 이름이 name인 항목을 가리킨다.                                                  |
| filename                | 파일명                                                                                      | None                        |                     | 데이터가 저장된 파일명. 파일의 포맷은 json 이어야 하며, 파일은 Texts 디렉토리에 들어있어야 한다.                                                       |
| alternate-name          | String                                                                                   | None                        |                     | sbml 파일을 선택할 때 사용할 가상의 이름.                                                                                         |
| catalog                 | String                                                                                   | None                        |                     | 데이터가 포함되어 있는 카탈로그의 ID.                                                                                             |
| subcatalog              | String                                                                                   | None                        |                     | 특정 카테고리가 포함되어 있는 서브카탈로그의 값. category의 값과 함께 사용된다.                                                                  |
| category                | String                                                                                   | None                        |                     | 데이터에서 특정 카테고리만을 선택할 때 지정함.                                                                                         |
| row-count               | Integer                                                                                  | 0                           |                     | 쇼케이스 행의 갯수. 0이면 행의 방향으로 무한대이다.                                                                                     |
| column-count            | Integer                                                                                  | 0                           |                     | 쇼케이스 열의 갯수. 0이면 열의 방향으로 무한대이다.                                                                                     |
| cell-size               | Size                                                                                     | "0, 0"                      | dp, em, layout의 상대값 | 셀 하나의 크기. 0이면 너비나 높이를 행이나 열의 개수로 1/n하여 자동으로 계산한다.                                                                  |
| cell-spacing            | Float                                                                                    | 0                           | dp, em, layout의 상대값 | 셀 간의 간격.                                                                                                           |
| content-margin          | Side                                                                                     | "0 0 0 0"                   | dp, em, layout의 상대값 | 헤더와 푸터를 제외한 콘텐트 영역의 상하좌우 여백. 축약형 사용 가능. 예) "1em", "1em 20dp", "1em 1.5em 0 1.2em"                                  |
| has-header              | Boolean                                                                                  | no                          |                     | 헤더를 포함하려면 yes를 지정함.                                                                                                |
| header-display-unit     | String                                                                                   | None                        |                     | 헤더에 사용할 데이터의 displayUnit 항목.                                                                                       |
| header-width            | Float                                                                                    | 0                           | dp, em, layout의 상대값 | 헤더의 너비. 0이면 자동계산.                                                                                                  |
| header-height           | Float                                                                                    | 0                           | dp, em, layout의 상대값 | 헤더의 높이. 0이면 자동계산.                                                                                                  |
| header-spacing          | Float                                                                                    | 0                           | dp, em, layout의 상대값 | 헤더와 셀 간의 간격.                                                                                                       |
| has-footer              | Boolean                                                                                  | no                          |                     | 푸터를 포함하려면 yes를 지정함.                                                                                                |
| footer-display-unit     | String                                                                                   | None                        |                     | 푸터에 사용할 데이터의 displayUnit 항목.                                                                                       |
| footer-width            | Float                                                                                    | 0                           | dp, em, layout의 상대값 | 푸터의 너비. 0이면 자동계산.                                                                                                  |
| footer-height           | Float                                                                                    | 0                           | dp, em, layout의 상대값 | 푸터의 높이. 0이면 자동계산.                                                                                                  |
| footer-spacing          | Float                                                                                    | 0                           | dp, em, layout의 상대값 | 푸터와 셀 간의 간격.                                                                                                       |
| has-toolbar             | Boolean                                                                                  | no                          |                     | 툴바를 포함하려면 yes를 지정함.                                                                                                |
| toolbar-display-unit    | String                                                                                   | None                        |                     | 툴바에 사용할 데이터의 displayUnit 항목.                                                                                       |
| toolbar-height          | Float                                                                                    | 0                           | dp, em, layout의 상대값 | 툴바의 높이. 0이면 자동계산.                                                                                                  |
| toolbar-position        | top / bottom                                                                             | bottom                      |                     | 툴바의 위치.                                                                                                            |
| auto-hides-toolbar      | Boolean                                                                                  | no                          |                     | 스크롤 시 자동으로 툴바가 사라지도록 하려면 yes를 지정한다.                                                                                |
| auto-minimizes-toolbar  | Boolean                                                                                  | no                          |                     | 스크롤 시 자동으로 툴바를 최소화 하려면 yes를 지정한다.                                                                                  |
| has-page-control        | Boolean                                                                                  | no                          |                     | 페이지 컨트롤을 포함하려면 yes를 지정함.                                                                                           |
| page-control-height     | Float                                                                                    | 0                           | dp, em, layout의 상대값 | 툴바의 높이. 0이면 자동계산.                                                                                                  |
| page-control-position   | left-top / left-bottom / right-top / right-bottom / top / right / bottom / left / center | bottom                      |                     | 페이지 컨트롤의 위치.                                                                                                       |
| page-control-margin     | Side                                                                                     | "0 0 0 0"                   | dp, em, layout의 상대값 | 페이지 콘트롤의 상하좌우 여백. 축약형 사용 가능. 예) "1em", "1em 20dp", "1em 1.5em 0 1.2em"                                             |
| inner-page-control      | Boolean                                                                                  | no                          |                     | 페이지 컨트롤을 쇼케이스 오브젝트 내로 배치하려면 yes를 지정한다.                                                                             |
| page-dot-size           | Size                                                                                     | "0, 0"                      | dp, em, layout의 상대값 | 페이지 점 이미지의 크기. "0, 0"이면 자동계산한다.                                                                                    |
| page-dot-spacing        | Float                                                                                    | 0                           | dp, em, layout의 상대값 | 페이지 점 사이의 간격.                                                                                                      |
| active-page-dot         | 파일명                                                                                      | None                        |                     | 활성화된 페이지 점 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                                                    |
| inactive-page-dot       | 파일명                                                                                      | None                        |                     | 비활성화된 페이지 점 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                                                   |
| sortable                | Boolean                                                                                  | no                          |                     | 해당 데이터의 정렬 기능을 지원하려면 yes를 지정한다.                                                                                    |
| sortkey                 | String                                                                                   | None                        |                     | 데이터 정렬에 사용할 키값. 데이터의 컬럼을 지정한다.                                                                                     |
| sortorder               | ascending / descending / random                                                          | ascending                   |                     | 데이터 정렬 시의 순서를 지정한다.                                                                                                |
| selectable              | Boolean                                                                                  | no                          |                     | 셀을 선택가능하게 하려면 yes를 지정한다.                                                                                           |
| selected-color          | Color                                                                                    | 투명                          |                     | 셀을 선택했을 때의 하이라이트 색상. 셀 전체가 하이라이트 된다.                                                                               |
| search-mode             | Boolean                                                                                  | no                          |                     | 검색 모드를 활성화하려면 yes를 지정한다.                                                                                           |
| clear-when-search       | Boolean                                                                                  | yes                         |                     | 검색 모드 시에 화면에서 셀을 사라지지 않도록 하려면 no를 지정한다.                                                                            |
| editing                 | Boolean                                                                                  | no                          |                     | 편집 모드를 활성화하려면 yes를 지정한다.                                                                                           |
| history-enabled         | Boolean                                                                                  | no                          |                     | 셀을 선택한 기록을 저장하려면 yes를 지정한다. 이 때, history 값을 함께 지정해야 한다.                                                            |
| history                 | String                                                                                   | None                        |                     | 셀 선택 기록을 저장하기 위한 임의의 식별자. history-enabled=yes일 때 사용된다.                                                             |
| series-mode             | Boolean                                                                                  | no                          |                     | 특정 시리즈와 그에 속한 아이템을 나열하기 위해 쇼케이스를 사용하려면 yes를 지정한다. 이 때, series의 값을 함께 지정해야 한다.                                      |
| series                  | String                                                                                   | None                        |                     | 시리즈 모드일 때 사용할 시리즈의 식별자.                                                                                            |
| max-cell-count          | Integer                                                                                  | 0                           |                     | 셀의 최대 갯수를 지정한다. 0이면 무제한.                                                                                           |
| first-cell              | Integer                                                                                  | 1                           |                     | 첫번째 셀의 index를 지정한다.                                                                                                |
| extends-data            | Boolean                                                                                  | no                          |                     | 셀 데이터의 내용을 확장하려면 yes를 지정한다. 셀 데이터에 포함된 상품 및 아이템, 시리즈, 멤버십, 포인트 등의 식별자를 이용해 해당 정보를 마켓 시스템으로부터 얻어와 데이터의 내용을 확장하게 된다. |
| data-downloadable       | Boolean                                                                                  | no                          |                     | 데이터를 외부에서 다운로드하려면 yes를 지정한다.                                                                                       |
| data-url                | URL                                                                                      | None                        |                     | 데이터를 다운로드 받을 URL. 이 때 다운로드되는 데이터의 형식은 json이어야 한다.                                                                  |
| data-path               | String                                                                                   | None                        |                     | 다운로드한 데이터 중 쇼케이스가 사용할 데이터의 루트를 지정한다.                                                                               |
| data-key                | String                                                                                   | None                        |                     | 다운로드한 데이터에서 id로 사용할 항목을 지정한다.                                                                                      |
| loads-more              | Boolean                                                                                  | no                          |                     | 데이터를 한 묶음씩 순차대로 다운로드하려면 yes를 지정한다.                                                                                 |
| more-count              | Integer                                                                                  | 쇼케이스 오브젝트의 3배 크기에 들어갈 셀의 갯수 |                     | 데이터를 한 묶음씩 불러올 때의 셀의 갯수.                                                                                           |
| download-path           | 디렉토리명                                                                                    | Downloads                   |                     | 쇼케이스 오브젝트를 통해 외부의 파일을 다운로드할 때 파일을 저장할 디렉토리명.                                                                       |
| eager-loading           | Boolean                                                                                  | no                          |                     | 쇼케이스 오브젝트가 로드될 때 셀을 모두 한꺼번에 로드하려면 yes를 지정한다.                                                                       |
| lazy-loading            | Boolean                                                                                  | yes                         |                     | 셀이 화면에 보이는 즉시 셀을 활성화하려면 no를 지정한다.                                                                                  |
| keeps-offscreen-cells   | Boolean                                                                                  | no                          |                     | 화면 밖으로 사라진 셀을 보관하여 다시 화면에 나타날 때 재사용하려면 yes를 지정한다.                                                                  |
| page-enabled            | Boolean                                                                                  | no                          |                     | 쇼케이스를 페이지 단위로 스크롤 하도록 하려면 yes를 지정한다.                                                                               |
| appearance              | String                                                                                   | None                        |                     | 쇼케이스의 모양을 지정하는 임의의 값. 해당 값은 $APPEARANCE라는 환경변수를 통해 헤더, 푸터, 툴바 및 모든 셀에 전달된다.                                        |
| focused-cell            | String                                                                                   | None                        |                     | 포커스된 셀을 가리키는 displayUnit 항목.                                                                                       |
| focus-when-loading      | Boolean                                                                                  | no                          |                     | 쇼케이스가 로드될 때, 포커스 셀로 이동하려면 yes를 지정한다.                                                                               |
| scroll-indicator-hidden | Boolean                                                                                  | no                          |                     | 스크롤 시 나타나는 스크롤바를 보이지 않게 하려면 yes를 지정한다.                                                                             |
| divider-image           | 파일명                                                                                      | None                        |                     | 행과 행 사이를 구분하는 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                                                 |
| divider-gravity         | left-top / left-bottom / right-top / right-bottom / top / right / bottom / left / center | center                      |                     | 행 구분 이미지가 배치될 위치.                                                                                                  |
| divider-size            | Size                                                                                     | "0, 0"                      |                     | 행 구분 이미지의 크기. 0이면 자동계산한다.                                                                                          |
| hidden-header-color     | Color                                                                                    | 투명                          |                     | 히든 헤더 영역의 배경색.                                                                                                     |
| hidden-footer-color     | Color                                                                                    | 투명                          |                     | 히든 푸터 영역의 배경색.                                                                                                     |
| hidden-header-image     | 파일명                                                                                      | None                        |                     | 히든 헤더 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.파                                                                        |
| hidden-footer-image     | 파일명                                                                                      | None                        |                     | 히든 푸터 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                                                         |
| has-own-navibar         | Boolean                                                                                  | no                          |                     | 셀을 선택하여 나타난 디테일 화면 또는 페이지 화면의 네비바를 별도로 정의하려면 yes를 지정한다.                                                            |
| hides-navibar           | Boolean                                                                                  | no                          |                     | 셀을 선택하여 나타난 디테일 화면 또는 페이지 화면의 네비바를 숨기려면 yes를 지정한다.                                                                 |
| has-own-title           | Boolean                                                                                  | no                          |                     | 셀을 선택하여 나타난 디테일 화면 또는 페이지 화면의 네비바의 제목을 셀의 데이터로부터 얻어내려면 yes를 지정한다.                                                  |
| expiry-labels-hidden    | Boolean                                                                                  | no                          |                     | 대여기간을 표시용 라벨을 숨기려면 yes를 지정한다.                                                                                      |

#### 액션 <a href="#_14" id="_14"></a>

| 액션           | 매개변수                                     | 설명                                                                                                                                                                                                                     |
| ------------ | ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| reload       |                                          | 오브젝트를 다시 로드한다.                                                                                                                                                                                                         |
| category     | category={CATEGORY}                      | 카테고리를 변경한다.                                                                                                                                                                                                            |
| search       | keyword={KEYWORD}                        | 쇼케이스를 검색 모드로 변경하고, keyword가 지정되어 있다면 검색을 시작한다.                                                                                                                                                                         |
| sort         | sortkey={SORTKEY}, sortorder={SORTORDER} | 쇼케이스를 sortkey와 sortorder를 이용하여 정렬한다.                                                                                                                                                                                   |
| appearance   | appearance={APPEARANCE}                  | 쇼케이스의 모양을 appearance의 값으로 변경한다.                                                                                                                                                                                        |
| next-page    |                                          | 쇼케이스의 다음 페이지로 이동한다. 쇼케이스가 page-enabled=yes인 경우에 동작한다.                                                                                                                                                                  |
| prev-page    |                                          | 쇼케이스의 이전 페이지로 이동한다. 쇼케이스가 page-enabled=yes인 경우에 동작한다.                                                                                                                                                                  |
| edit         |                                          | 쇼케이스를 편집 모드로 전환한다.                                                                                                                                                                                                     |
| edit-done    |                                          | 쇼케이스의 편집 모드를 종료한다.                                                                                                                                                                                                     |
| select       | number={NUMBER}                          | number로 지정된 셀을 선택한다.                                                                                                                                                                                                   |
| deselect     | number={NUMBER}                          | number로 지정된 셀의 선택을 해제한다.                                                                                                                                                                                               |
| select-all   |                                          | 모든 셀을 선택한다.                                                                                                                                                                                                            |
| deselect-all |                                          | 모든 셀의 선택을 해제한다.                                                                                                                                                                                                        |
| remove       | display-unit=${DISPLAY\_UNIT}            | display-unit으로 지정된 셀을 삭제한다. 만약 display-unit이 지정되어 있지 않다면 현재 선택된 모든 셀을 삭제한다.                                                                                                                                            |
| shows-expiry |                                          | 셀에 포함되어 있는 대여기간 라벨을 보여준다.                                                                                                                                                                                              |
| hides-expiry |                                          | 셀에 포함되어 있는 대여기간 라벨을 숨긴다.                                                                                                                                                                                               |
| open         | item=next/prev                           | 쇼케이스에 지정되어 있는 시리즈의 아이템 중 가장 최근에 읽은 아이템을 오픈한다. series-mode=yes일 때 동작한다. 만약 item을 next로 지정했다면 최근 아이템의 다음 아이템을 오픈하고, prev로 지정했다면 최근 아이템의 이전 아이템을 오픈한다.                                                                    |
| purchase     | points={POINTS}, product-key={KEY}       | 쇼케이스의 모든 셀과 연관된 상품을 구매한다. 만약 쇼케이스가 편집 모드라면 현재 선택되어 있는 셀과 연관된 상품을 구매한다. 셀과 연관된 상품이란 셀의 데이터 중 product 항목을 가리킨다. 만약 product-key가 지정되어 있다면 셀의 데이터 중 product-key로 지정된 항목을 가리킨다. 이 때, points가 지정되어 있다면 구매시 지정된 points를 이용한다. |

#### 이벤트 <a href="#_15" id="_15"></a>

| 이벤트 액션명              | 설명                       |
| -------------------- | ------------------------ |
| action-when-selected | 셀을 눌러 선택된 상태가 되었을 때 발생함. |

#### 외부 데이터를 사용하는 방법 <a href="#_16" id="_16"></a>

쇼케이스 오브젝트는 외부 데이터를 사용하여 셀의 내용을 채워넣는 기능을 지원한다. 외부 데이터는 웹(HTTP/S)을 통해 액세스 가능해야 하며, 요청에 대한 응답으로 json으로 표현된 데이터를 전송해야 한다. 웹 요청은 POST 방식을 사용하며, 요청하는 데이터의 범위(시작위치, 갯수)를 파라미터로 전달할 수 있다. 요청받은 범위가 실제 데이터의 범위를 벗어나면, 빈 json 데이터와 함께 성공 응답(200)을 해야 한다. 데이터 범위를 파라미터로 전달하지 않으면, 모든 데이터를 한번에 포함하여 응답한다. 쇼케이스 오브젝트에서 외부 데이터를 사용하려면 data-downloadable을 yes로 지정하고, data-url 속성에 외부 데이터의 URL을 지정하면 된다. 쇼케이스 오브젝트에 Load more 기능이 활성화되어 있다면(loads-more=yes), 데이터의 범위를 지정하여 외부 데이터를 순차적으로 한 묶음씩 불러올 수 있다.

```javascript
=object showcase: name="magazine", data-downloadable=yes, \
                data-url="http://www.munhak.com/magazine", loads-more=yes
```

### 카드(Card) 오브젝트 <a href="#card" id="card"></a>

#### 사용예 <a href="#_17" id="_17"></a>

```
=object card: name="baseball"
```

#### 속성 <a href="#_18" id="_18"></a>

| 속성                    | 타입(허용값)                                                                                  | 기본값       | 단위                  | 설명                                                                     |
| --------------------- | ---------------------------------------------------------------------------------------- | --------- | ------------------- | ---------------------------------------------------------------------- |
| name                  | String                                                                                   | None      |                     | 데이터의 이름. 로컬 데이터베이스의 collections 테이블에서 collection의 이름이 name인 항목을 가리킨다.  |
| filename              | 파일명                                                                                      | None      |                     | 데이터가 저장된 파일명. 파일의 포맷은 json 이어야 하며, 파일은 Texts 디렉토리에 들어있어야 한다.           |
| alternate-name        | String                                                                                   | None      |                     | sbml 파일을 선택할 때 사용할 가상의 이름.                                             |
| catalog               | String                                                                                   | None      |                     | 데이터가 포함되어 있는 카탈로그의 ID.                                                 |
| subcatalog            | String                                                                                   | None      |                     | 특정 카테고리가 포함되어 있는 서브카탈로그의 값. category의 값과 함께 사용된다.                      |
| category              | String                                                                                   | None      |                     | 데이터에서 특정 카테고리만을 선택할 때 지정함.                                             |
| cell-spacing          | Float                                                                                    | 0         | dp, em, layout의 상대값 | 카드 셀 간의 간격.                                                            |
| has-page-control      | Boolean                                                                                  | no        |                     | 페이지 컨트롤을 포함하려면 yes를 지정함.                                               |
| page-control-height   | Float                                                                                    | 0         | dp, em, layout의 상대값 | 툴바의 높이. 0이면 자동계산.                                                      |
| page-control-position | left-top / left-bottom / right-top / right-bottom / top / right / bottom / left / center | bottom    |                     | 페이지 컨트롤의 위치.                                                           |
| page-control-margin   | Side                                                                                     | "0 0 0 0" | dp, em, layout의 상대값 | 페이지 콘트롤의 상하좌우 여백. 축약형 사용 가능. 예) "1em", "1em 20dp", "1em 1.5em 0 1.2em" |
| inner-page-control    | Boolean                                                                                  | no        |                     | 페이지 컨트롤을 쇼케이스 오브젝트 내로 배치하려면 yes를 지정한다.                                 |
| page-dot-size         | Size                                                                                     | "0, 0"    | dp, em, layout의 상대값 | 페이지 점 이미지의 크기. "0, 0"이면 자동계산한다.                                        |
| page-dot-spacing      | Float                                                                                    | 0         | dp, em, layout의 상대값 | 페이지 점 사이의 간격.                                                          |
| active-page-dot       | 파일명                                                                                      | None      |                     | 활성화된 페이지 점 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                        |
| inactive-page-dot     | 파일명                                                                                      | None      |                     | 비활성화된 페이지 점 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                       |

#### 액션 <a href="#_19" id="_19"></a>

| 액션     | 매개변수 | 설명             |
| ------ | ---- | -------------- |
| reload |      | 오브젝트를 다시 로드한다. |

#### 이벤트 <a href="#_20" id="_20"></a>

N/A

### 리스트(List) 오브젝트 <a href="#list" id="list"></a>

#### 사용예 <a href="#_21" id="_21"></a>

```
=object list: name="booklist"
```

#### 속성 <a href="#_22" id="_22"></a>

| 속성             | 타입(허용값) | 기본값  | 단위                  | 설명                                                                    |
| -------------- | ------- | ---- | ------------------- | --------------------------------------------------------------------- |
| name           | String  | None |                     | 데이터의 이름. 로컬 데이터베이스의 collections 테이블에서 collection의 이름이 name인 항목을 가리킨다. |
| filename       | 파일명     | None |                     | 데이터가 저장된 파일명. 파일의 포맷은 json 이어야 하며, 파일은 Texts 디렉토리에 들어있어야 한다.          |
| alternate-name | String  | None |                     | sbml 파일을 선택할 때 사용할 가상의 이름.                                            |
| catalog        | String  | None |                     | 데이터가 포함되어 있는 카탈로그의 ID.                                                |
| subcatalog     | String  | None |                     | 특정 카테고리가 포함되어 있는 서브카탈로그의 값. category의 값과 함께 사용된다.                     |
| category       | String  | None |                     | 데이터에서 특정 카테고리만을 선택할 때 지정함.                                            |
| cell-spacing   | Float   | 0    | dp, em, layout의 상대값 | 리스트 셀 간의 간격.                                                          |

#### 액션 <a href="#_23" id="_23"></a>

| 액션     | 매개변수 | 설명             |
| ------ | ---- | -------------- |
| reload |      | 오브젝트를 다시 로드한다. |

#### 이벤트 <a href="#_24" id="_24"></a>

N/A

### 셀(Cell) 오브젝트 <a href="#cell" id="cell"></a>

#### 사용예 <a href="#_25" id="_25"></a>

```
=object cell: display-unit="S_BOOKS_001"
```

#### 속성 <a href="#_26" id="_26"></a>

| 속성                | 타입(허용값) | 기본값  | 단위 | 설명                                                           |
| ----------------- | ------- | ---- | -- | ------------------------------------------------------------ |
| display-unit      | String  | None |    | 데이터의 displayUnit 항목.                                         |
| filename          | 파일명     | None |    | 데이터가 저장된 파일명. 파일의 포맷은 json 이어야 하며, 파일은 Texts 디렉토리에 들어있어야 한다. |
| alternate-name    | String  | None |    | sbml 파일을 선택할 때 사용할 가상의 이름.                                   |
| catalog           | String  | None |    | 데이터가 포함되어 있는 카탈로그의 ID.                                       |
| data-downloadable | Boolean | no   |    | 데이터를 외부에서 다운로드하려면 yes를 지정한다.                                 |
| data-url          | URL     | None |    | 데이터를 다운로드 받을 URL. 이 때 다운로드되는 데이터의 형식은 json이어야 한다.            |
| data-path         | String  | None |    | 다운로드한 데이터 중 셀이 사용할 데이터의 루트를 지정한다.                            |
| data-key          | String  | None |    | 다운로드한 데이터에서 id로 사용할 항목을 지정한다.                                |
| lazy-loading      | Boolean | yes  |    | 셀이 화면에 보이는 즉시 셀을 활성화하려면 no를 지정한다.                            |

#### 액션 <a href="#_27" id="_27"></a>

| 액션     | 매개변수 | 설명             |
| ------ | ---- | -------------- |
| reload |      | 오브젝트를 다시 로드한다. |

#### 이벤트 <a href="#_28" id="_28"></a>

N/A
