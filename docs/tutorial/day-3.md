# 쇼케이스 오브젝트 Day 3

### 카테고리 분류

category 옵션을 이용해 data를 분류하는 방법에 대하여 설명합니다.

object showcase는 cell들로 구성되었으며, 각 cell은 데이터 연결에 있어 display-unit 옵션을 사용합니다.

object showcase에서의 name 옵션으로 1차 데이터를 필터링하고 이 데이터들을 category 옵션으로 2차 데이터 필터링을 진행합니다.

이렇게 최종 필터링된 데이터들의 id는 cell의 display-unit에 연결되어 sbml 화면으로 나타나게 됩니다.

<figure><img src="images/image (23).png" alt=""><figcaption></figcaption></figure>

### 구글 드라이브 실시간 연동

showcase의 데이터는 구글 스프레드시트에서도 관리할 수 있습니다.

js에서 구글 스프레드시트의 데이터를 api처럼 가져올 수 있습니다. 동일한 데이터가 sqlite에 포함되어 있더라도 구글 스프레드시트가 우선됩니다.

<figure><img src="images/image (16).png" alt=""><figcaption></figcaption></figure>

#### 1) 필요 모듈 다운로드

프로젝트에서 이미지 리소스를 끌고 올 때, 프로젝트 구조에서 Images 폴더에 해당 image 리소스를 넣은 후, sbml에서 image 리소스명을 통해 불러왔던 것을 기억하실 겁니다.

이와 마찬가지로 Google Drive를 해당 프로젝트에서 데이터로 사용하는 api로 가져오기 위해서 특정한 모듈을 이용해야 합니다. 그 과정을 위해서 아래의 url을 이용할 수 있습니다.

{% embed url="https://github.com/jamkit-modules" %}

다양한 모듈 중 google-sheets 연동을 위한 모듈을 사용해야 하기 때문에, 아래와 같이 google-sheets 레포지터리를 들어간 뒤, 해당 Project를 다운로드 혹은 clone합니다.\


<figure><img src="images/image (29).png" alt=""><figcaption></figcaption></figure>

#### 2) 프로젝트에 모듈 추가

MainApp 폴더에 Scripts 폴더를 만든 후, 다운로드한 모듈을 추가합니다.

<figure><img src="images/image (11).png" alt=""><figcaption></figcaption></figure>

#### 3) JS 연결

catalog\_home.sbml에서 object showcase를 사용하기에, catalog\_home.js 파일을 생성합니다.

* 구글 스프레드시트
  * "파일 > 공유 > 다른 사용자와 공유 > 일반 액세스"가 **'링크가 있는 모든 사용자'**로 설정합니다.
* js 파일
  * function에 **해당 구글 스프레드시트 url의 id 부분**을 삽입합니다.
  * function에 **해당 구글 스프레드 시트의 sheet 이름**을 일치시킵니다
* showcase object
  * `data-script="feed_apps"` 속성을 추가합니다.

<figure><img src="images/스크린샷 2022-12-07 오후 5.56.42.png" alt=""><figcaption><p>구글 스프레드시트</p></figcaption></figure>

<figure><img src="images/image (2).png" alt=""><figcaption><p>js 파일</p></figcaption></figure>

<figure><img src="images/스크린샷 2022-12-07 오후 5.21.02.png" alt=""><figcaption><p>showcase object</p></figcaption></figure>

### object showcase 추가 속성

#### ViewPager

* page-enabled=yes

<figure><img src="images/image (22).png" alt=""><figcaption></figcaption></figure>

페이지를 넘기듯 자연스럽게 다음의 cell을 보여주는 설정입니다.

터치 슬라이딩을 통해서 페이지가 넘겨지기에 page-enabled=yes 옵션을 줄 시, object showcase의 width와 height와 동일한 값으로 cell-size 값을 설정해야 하나의 페이지에서 하나의 cell을 나타낼 수 있습니다.

{% code overflow="wrap" %}
```javascript
//sbss (object showcase에 연결된 style)
#showcase_list: width=0.9pw, height=0.8ph, \
                cell-size="0.9pw 0.8ph", 
page-enabled=yes, \
                row-count=1, preload-count=1, keep-count=1
```
{% endcode %}

#### ViewPager + indicator

<figure><img src="images/image (25).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="188">속성</th><th>설명</th></tr></thead><tbody><tr><td>has-page-control</td><td><p><strong>현 페이지의 위치를 알 수 있는 indicator 사용 여부 설정</strong></p><p>💡 default 값 has-page-control=no</p></td></tr><tr><td>active-page-dot</td><td><p><strong>활성화 페이지일 시, 사용할 리소스 설정</strong></p><p>💡 has-page-control=yes 설정 필요</p></td></tr><tr><td>inactive-page-dot</td><td><p><strong>비활성화 페이지일 시, 사용할 리소스 설정</strong></p><p>💡 has-page-control=yes 설정 필요</p></td></tr><tr><td>page-dot-size</td><td><p><strong>page-control의 리소스들의 사이즈 설정</strong></p><p>💡 has-page-control=yes 설정 필요</p></td></tr><tr><td>page-dot-spacing</td><td><p><strong>page-control의 리소스들 간의 간격 설정</strong></p><p>💡 has-page-control=yes 설정 필요</p></td></tr><tr><td>page-control-position</td><td><p><strong>page-control의 위치 설정 { top, left, bottom, right 등}</strong></p><p>💡 has-page-control=yes 설정, (in)active-page-dot=”[파일명.확장자] 필요</p></td></tr><tr><td>inner-page-control</td><td><p><strong>page-control을 cell의 내부에 위치시킬지 여부 설정</strong></p><p>💡 default 값 inner-page-control=no</p><p>💡 has-page-control=yes 설정,</p><p>(in)active-page-dot="파일명" 필요</p></td></tr></tbody></table>

(예제 1) page-control을 cell 외부에 배치

{% code overflow="wrap" %}
```javascript
// SBML
=begin list
=
object showcase: data-script="feed_apps", alternate-name=apps, \
                
style=showcase_list
=end list

// SBSS
#showcase_list: width=0.9pw, height=0.8ph, \
                
preload-count=1, keep-count=1, row-count=1, \
                
cell-size="0.9pw 0.8ph", max-cell-count=5, \
                page-enabled=yes, has-page-control=yes, \
                
active-page-dot="circle.png", \
                inactive-page-dot="rec.png", \
                
page-dot-size="10dp 10dp", 
page-dot-spacing=10dp
```
{% endcode %}

![](<images/image (10).png>)

위의 스타일에서 page-control-position 옵션이 default 값으로 bottom으로 되어 있기에, page-control-position="top" / page-control-position="right" / page-control-positon="left" 등의 설정으로 외부의 page-control 위치를 변경할 수 있습니다.

(예제 2) page-control을 cell 내부에 배치

{% code overflow="wrap" %}
```javascript
// SBML
=begin list
=object showcase: data-script="feed_apps", \
                                                                
alternate-name=apps, \
style=showcase_list
=end list

// SBSS
#showcase_list: width=0.9pw, height=0.8ph, \
                
preload-count=1, keep-count=1, row-count=1, \
                
cell-size="0.9pw 0.8ph", max-cell-count=5, \
                page-enabled=yes, has-page-control=yes, \
                
active-page-dot="circle.png", \
                inactive-page-dot="rec.png", \
                
page-dot-size="10dp 10dp", \
                
page-dot-spacing=10dp, inner-page-control=yes
```
{% endcode %}

![](<images/image (15).png>)

### object showcase header 설정

* has-header=yes
* header-height
* header-width

has-header=yes일 경우, 파일 이름 규칙에 따라 header sbml 파일을 탐색한 후 object showcase의 header 영역에 sbml 파일이 구현됩니다.

<figure><img src="images/image (13).png" alt=""><figcaption></figcaption></figure>

또한 특정 sbml파일을 연결할 경우 `header-display-unit={id}` 설정을 사용할 수 있습니다.

{% hint style="info" %}
**파일 이름 규칙**

* display-unit을 지정할 경우 (has-own-sbml=yes)\
  <mark style="color:red;">{display-unit}</mark>\_header.sbml
* template을 지정할 경우\
  showcase\_<mark style="color:red;">{name}</mark>\_<mark style="color:red;">{template}</mark>\_header.sbml
* showcase name을 지정할 경우\
  showcase\_<mark style="color:red;">{name}</mark>\_header.sbml
{% endhint %}

{% hint style="info" %}
**column과 row 개수에 따른 설정**

* column-count=1로 설정했을 경우, 스크롤이 상하로 생깁니다.\
  **header-height 옵션을 사용해야 함.**
* row-count=1로 설정했을 경우, 스크롤이 좌우로 생깁니다.\
  **header-width 옵션을 사용해야 함.**
{% endhint %}

### object showcase footer 설정

* has-footer=yes
* footer-height
* footer-width

has-footer=yes일 경우, 파일 이름 규칙에 따라 footer sbml 파일을 탐색한 후 object showcase의 footer 영역에 sbml 파일이 구현됩니다.

<figure><img src="images/image (12).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**column과 row 개수에 따른 설정**

* column-count=1로 설정했을 경우, 스크롤이 상하로 생깁니다.\
  **footer-height 옵션을 사용해야 함.**
* row-count=1로 설정했을 경우, 스크롤이 좌우로 생깁니다.\
  **footer-width 옵션을 사용해야 함.**
{% endhint %}

### object showcase toolbar 설정

* has-toolbar=yes
* footer-height
* footer-width

has-toolbar=yes일 경우, 파일 이름 규칙에 따라 toolbar sbml 파일을 탐색한 후 object showcase의 toolbar 영역에 sbml 파일이 구현됩니다.

<figure><img src="images/image (5).png" alt=""><figcaption></figcaption></figure>

toolbar의 경우 header와 footer에서 row-count, column-count 설정에 따른 페이지 스크롤 방향에 맞게 width, height 값을 설정해야 하는 것과는 다르게 width는 object showcase의 width와 동일하게 설정되고, height 값만 설정 가능합니다. 따라서 toolbar를 사용할 경우, cell-size에서 toolbar의 height를 빼야 합니다.

{% code overflow="wrap" %}
```javascript
// showcase의 sbss
#showcase_list: width=0.9pw, height=0.8ph, \
                
..., \
                cell-size="0.9pw 0.8ph-20dp", \
                
has-toolbar=yes, toolbar-height=20dp
```
{% endcode %}

toolbar-postion 옵션을 이용해서 default bottom인 값을 변경할 수 있습니다.

```javascript
// showcase의 sbss
#showcase_list: width=0.9pw, height=0.8ph, \
                ..., \
                has-toolbar=yes, toolbar-position="top"
```
