# 레이아웃 다루기 Day 2

### Section을 Object처럼 처리하기

```javascript
// SBML
=begin test
섹션 내용
=end test

// SBSS
/test: display=block, position=absolute, gravity=center, \
        x=100dp, y=30, pack=yes, background-color=#FFCC
```

* object는 기본적으로 block 처리가 되어 있지만, section은 그렇지 않다. object과 같이 block 처리를 해주기 위해서는 `display=block`을 적용하면 된다.
* 또한 section은 width의 기본 값이 1pw이기에, section 내의 텍스트가 차지하는 영역의 크기에 맞추기 위해서 `pack=yes` 속성을 적용할 수 있다. (padding 영역을 포함)
* `position=absolute`를 적용할 때, `gravity`나 `x,y` 속성을 통해서 section의 위치를 화면 내에서 자유롭게 배치할 수 있다.

### Section 숨기기

```javascript
=begin test: display=none
섹션 내용
=end test
```

* section에 `display=none` 스타일을 적용하면, 해당 섹션의 width, height를 포함해 보이지 않게 된다.

### Object 숨기기

```javascript
// 방법 1: hidden=yes
=object image: filename="check.png", width=50dp, hidden=yes

// 방법 2: alpha=0

=object image: filename="check.png", width=50dp, alpha=0

// 방법 3: display=none
=object image: filename="check.png", width=50dp, display=none
```

* hidden=yes
  ⇒ 오브젝트가 화면에서 보이지 않지만 width와 height가 그대로 남아 있다.
* alpha=0
  ⇒ 투명도를 조절하는 스타일 속성으로, 오브젝트가 화면에서 보이지 않지만 width와 height가 그대로 남아 있다.
* display=none
  ⇒ 오브젝트가 화면에서 보이지 않으며, width와 height까지 없어진다.

### 화면 내 독립적인 레이아웃을 불러오는 방법

```javascript
// 방법 1: object sbml
=object sbml: filename={filename.sbml}

// 방법 2: object section
=object section: section={id}

// 방법 3: object cell (container object)
=object cell: display-unit={id}
```

* object sbml, object section은 레이아웃(sbml, sbss)만 올릴 수 있다.
  * ![](images/object-sbml-section.png)
* object cell은 레이아웃뿐만 아니라 스크립트(js)도 올릴 수 있다.
  * `display-unit`은 독립적인 sbml/sbss/js를 연결시켜주는 고리이며, 해당 속성을 사용하기 위해서는 파일의 이름 규칙을 알아야 한다.
  * ![](images/object-cell.png)

### Object Cell

```javascript
=begin catalog
=begin body


=object cell: display-unit="S_WELCOME", width=0.5pw, height=0.5ph

=end body

=end catalog
```

* `object cell`을 불러오기 위해서는 `display-unit`을 사용해야 한다.
* `display_unit`에 파일의 이름을 연결하는 것으로, `object cell`을 사용하기 위해서는 반드시 `ABC_cell.sbml` `ABC_cell.sbss`와 같이 파일명이 `{display-unit}_cell`로 정의되어야 한다.
* 또한 반드시 `width`와 `height` 속성을 주어야 한다.
* ![](images/display-unit.png)

### Object Cell 구현 예시

* 예시 1: 확인을 위해 blank로 화면 채움

```javascript
=begin cell

=object blank: width=1pw, height=1ph, background-color=#FFCCFF
=end cell
```

* 예시 2: `${__DATA__}`을 섹션 내에 입력할 경우 `S_WELCOME_cell`의 환경 설정 내용이 나온다.

```javascript
=begin cell: background-color=#FFCCFF
${__DATA__}
=end cell
```

![](images/object-cell-ex2.png)

* 예시 3: `${__DATA__}`의 데이터를 가져오는 방법은 `${변수명}`을 사용함

```javascript
=begin cell: background-color=#FFCCFF
${YEAR}년 ${MONTH}월 ${DAY}일 ${id}를 이용해 object cell 파악하기
=end cell
```

![](images/object-cell-ex3.png)

### Object Cell에 JS를 적용한 독립적인 레이아웃

* S_WELCOME_cell.js 파일 만들기
* `on_load` 함수 만들기 ⇒ `controller.action의 alert`로, 독립적인 context 적용을 확인하는 용도
* S_WELCOME_cell.sbml에 script 연결
* ![](images/object-cell-js.png)

#### S_WELCOME_cell.js

```javascript
function on_load() {
    controller.action("alert", {"message": "catalog_test에서의 alert"})
    }
```

#### S_WELCOME_cell.sbml

* `script-when-loaded`는 화면이 올라올때 script가 작동되는 것(jquery의 `document.ready` 유사)

```javascript
=begin cell: background-color=#FFCCFF, script-when-loaded=on_load
${YEAR}년 ${MONTH}월 ${DAY}일 ${id}를 이용해 object cell 파악하기
=end cell
```

#### 화면 실행결과: 두 개의 alert이 뜸

![](images/object-cell-js-result1.png)

![](images/object-cell-js-result2.png)

# 실습하기

### 아래의 화면을 구현해보세요

<figure><img src="images/layout-practice-2.jpg" alt=""><figcaption></figcaption></figure>

### 실습 가이드

#### 개요

* 섹션 속성은 [basic-style.md](../../reference/basic-style.md "mention") 또는 [이 문서](https://bookjam.github.io/jamkit/refs_styles/)를 참고하세요.
* 오브젝트 속성은 [basic-object.md](../../reference/basic-object.md "mention") 또는 [이 문서](https://bookjam.github.io/jamkit/refs_objects/)를 참고하세요.
* jamkit으로 "practice" 프로젝트를 생성하고, cataog_home.sbml과 sbss의 본문을 지우고 작업하세요.
* 필요한 이미지는 [이 파일](https://bpmgbiz.sharepoint.com/:u:/s/BPMG_Lecture/ERTA2vt4vXJBjKH8_GhYN-IBfIiZ-hNyM4lM2XsMnG2v_A?e=ii1RT6)을 다운로드하세요.
* 디바이스나 emulator를 실행하여 직접 화면을 보면서 작업하세요.
* label, textfield, button 등의 오브젝트는 width, height 둘 다 반드시 지정해야 구현됩니다.

#### **작업 순서**

{% hint style="info" %}
catalog_home.sbml에서 catalog 섹션 내에서 아래의 섹션들을 구현합니다.
{% endhint %}

* catalog_home.sbml
  * (판매상품이미지) **top 섹션**을 만들고 image, button 오브젝트를 구현합니다.
  * (판매자) **seller 섹션**을 만들고 image, label, button 오브젝트를 구현합니다.
  * (판매상품소개) **product 섹션**을 만들고 label, blank 오브젝트를 구현합니다.
  * (좋아요/댓글) **communicate 섹션**을 만들고 label과 button 오브젝트를 구현합니다.
  * 위의 섹션들을 **object section**과 연결합니다.
  * (문의) **object cell**을 구현합니다.
* S__INQUIRE_cell.sbml_
  * (하트) **right 섹션**을 만들고, checkbox 오브젝트를 구현합니다.
  * (문의) **left 섹션**을 만들고, button 오브젝트를 구현합니다.

### 최종 결과 파일

* 이 [폴더](https://bpmgbiz.sharepoint.com/:f:/s/BPMG_Lecture/Ev8bHqTIvM1JgRIu_t1RsNcBY0vVGnrlxil9jkBu_Pg_KQ?e=Gw7D52)의 [레이아웃 다루기 Day 2_실습하기.zip](https://bpmgbiz.sharepoint.com/:u:/s/BPMG_Lecture/EWC3CZZ_cPhBht2lQHGIXUsBvu4tD5iYSabnkXLPlAaQrg?e=EPajyG)을 다운로드해서 확인해보세요.

### 구현 가이드

{% hint style="info" %}
레이아웃 다루기 Day 2의 내용에 중점을 맞춰 tip 내용이 기재되어 있습니다.
{% endhint %}

* **catalog_home.sbml**

<details>

<summary>top 섹션 구현</summary>

&#x20;                                       ![](images/layout-practice2-top.jpg)

#### sbml

```
// top section

=comment: 이미지, 버튼들
=begin top
=object image: filename="mayibe.jpg", style=img_product
=object button: image="icon_close_w.png", style=btn_close
=object button: image="icon_share_w.png", style=btn_share
=object button: image="icon_more_vertical_w.png", style=btn_more
=end top
```

#### sbss

```
// top sbss

/catalog/top:display=block, positon=abs, gravity=top, margin-top=22dp

#img_product: width=1pw, height=0.9pw, scale-mode=fill
#btn_close: width=25dp, position=abs, x=10dp, y=5dp
#btn_share: width=25dp, position=abs, gravity=right-top, x=-50dp, y=5dp
#btn_more: width=25dp, position=abs, gravity=right-top, x=-10dp, y=5dp
```

#### tip

* 나중에 정의 오브젝트로 덮어 씌어지기 때문에, button들이 img 오브젝트 위에 있습니다.
* top.right섹션에서의 버튼들이 인라인오브젝트 버튼들의 간격을 띄우기 위해선 margin-right 혹은 margin-left를 적용합니다

</details>

<details>

<summary>seller 섹션 구현</summary>

#### &#x20;                                            ![](images/layout-practice2-seller.jpg)

#### sbml

```
// seller sbml

=begin seller
=begin seller.left
=object button: image="icon_profile.jpg", style=img_seller
=end seller.left

=begin seller.center
=object label: text="메이아이비", style=lb_seller_name
=object label: text="성내동 . 단골 22", style=lb_seller_detail
=end seller.center

=begin seller.right
=(object image: filename="plus.png", style=img_seller_plus)=\
=(object button: label="단골 맺기", style=btn_seller_plus)=
=end seller.right
=end seller
```

#### sbss

```
// seller sbss

--seller
/catalog/seller:  display=block, height=70dp, border-bottom-width=1dp, border-bottom-color=#D3CFCFAB, margin="10dp 15dp"
/catalog/seller/seller.left: display=block, position=abs, width=80dp
/catalog/seller/seller.center: display=block, position=abs, width=200dp, height=60dp, x=200, y=35
/catalog/seller/seller.right:  display=block, position=abs, width=100dp, x=1pw-340, y=35, \
                            padding="8dp 0", background-color=#FF6D0C, border-radius=15%, text-align=center
    
#img_seller: width=60dp, height=60dp, align=left, content-border-radius=100%, content-border-width=1dp, content-border-color=#777575AB
#lb_seller_name: font-weight=bold, align=left
#lb_seller_detail: text-color=#6B6969AB, font="bold 0.9 sans-serif", margin-top=8dp, align=left

#img_seller_plus: width=9dp, margin-right=8dp, vertical-align=middle
#btn_seller_plus: label-font-size=0.8, font-weight=bold, label-color=#FFFFF, vertical-align=middle


```

#### tip

* seller.right섹션의 경우 아이콘과 버튼을 함께 정렬해야 하기에, 섹션 전체를 버튼처럼 보이게 처리합니다.

</details>

<details>

<summary>product 섹션 구현</summary>

&#x20;                                               ![](images/layout-practice2-product.jpg)

#### sbml

```
// product sbml

=comment: 판매상품 상세
=begin product
=object label: text="꽃 정기구독 화병꽂이 🍠", style=lb_product_title
=(object label: text="꽃집/꽃배달",style=common_product)= \
=(object blank: style=blk_product)= \
=(object label: text="1일 전", style=common_product)= 

화이트 + 레드 포인트로 제작한 꽃 정기구독 화병꽂이 입니다.
\n
=object label: text="조회 29", style=lb_product_lookup
\n
=end product
```



#### sbss

```
// product sbss

--product
/catalog/product: border-bottom-width=1dp, border-bottom-color=#D3CFCFAB, margin="10dp 15dp"

#common_product: text-color=#6B6969AB, vertical-align=middle, font-size=0.8, font-weight=bold, align=left
#lb_product_title: style=common_product, margin="10dp 0", font-size=1.2, text-color=#000000
#blk_product: content-background-color=#6B6969AB, width=2dp, height=2dp, vertical-align=middle
#lb_product_lookup: font-size=0.8, font-weight=bold, align=left, text-color=#6B6969AB

```

</details>

<details>

<summary>communicate 섹션 구현</summary>

#### &#x20;                                              ![](images/layout-practice2-communicate.jpg)

#### sbml

```
// communicate sbml

=comment: 좋아요, 댓글
=begin communicate
=begin communicate.like
=(object button: image="like.png", width=15dp)= \
=(object label: text="좋아요 2", style=communicate.btn)=
=end communicate.like

=begin communicate.comment
=(object button: image="chat.png", width=15dp)= \
=(object label: text="댓글", style=communicate.btn)=
=end communicate.comment
=end communicate
```

#### sbss

```
// communicate sbss

--communicate
/catalog/communicate: display=block, height=30dp, border-bottom-width=1dp, border-bottom-color=#D3CFCFAB, margin="10dp 15dp"
/catalog/communicate/communicate.like: display=block, position=abs, width=70dp
/catalog/communicate/communicate.comment: display=block, position=abs, width=50dp, x=80dp

#communicate.btn: font-size=0.9, text-color=#6B6969AB
```

#### tip

* communicate 섹션을 display=block 하지 않을 경우, 하위 섹션인 like과 comment가 position=abs에 의해 communicate 섹션의 영역 범위를 벗어납니다.
* communicate 섹션을 display=block 하였어도 하위 섹션인 like, comment에 현재 스타일 gravity를 추가할 경우 communicate 섹션의 영역 범위를 벗어납니다.

</details>

<details>

<summary>object section 연결</summary>

object section 연결 이유는&#x20;

bottom에 고정되어 있는 object cell의 위치를 제외한 영역에서&#x20;

스크롤이 적용되도록 하기 위해서 입니다.

#### sbml

```
// object section

=object section: section=section.view, width=1pw, height=0.93ph

=begin catalog: id=section.view, display=none
=begin top
...
=end top

=begin seller
...
=end seller

=begin product
...
=end product

=begin communicate
...
=end communicate
=end catalog
```

#### tip

* catalog section id와 object section의 section이 일치해야 합니다.
* object section의 width는 전체 너비여야 하기에 1pw으로 해야 합니다.
* object section의 height는 object cell가 들어갈 높이를 고려해야 하기에, 1ph가 아닙니다.

</details>



* **S_**_**INQUIRE_cell**_

<details>

<summary>left, right 섹션 구현</summary>

#### sbml

```
=begin cell

=begin left
=object checkbox: id="heart", style=chk_heart
=end left
=begin right
=(object button: label="전화문의", script=on_click_tel, style=btn_phone)=\
=(object button: label="채팅문의", script=on_click_chat, style=btn_chat)=
=end right

=end cell
```

#### sbss

```
/cell: border-top-width=2dp, border-top-color=#A8A6A6AB
/cell/left: display=block, position=abs, width=0.1pw, gravity=left, x=30
/cell/right: display=block, position=abs, width=0.9pw, gravity=right,  x=-30, text-align=right


#common.style:  width=45%, height=0.08pw, content-border-width=1dp, content-border-radius=8dp, content-border-color=#D3CFCFAB
#btn_phone: style=common.style, margin="0 10dp"
#btn_chat: style=common.style, content-background-color=#FF6D0, label-color=#FFFFFF, content-background-color=#FF6D0C
#chk_heart: image="heart_gray.png", width=0.05pw, selected-image="heart_red.png"
```

#### js

```javascript
function on_click_tel() {
     controller.action("alert", {"message": "전화 문의 팝업"})
}

function on_click_chat() {
     controller.action("alert", {"message": "채팅 문의 팝업"})
}

```

</details>

* **object cell**&#x20;

<details>

<summary>object cell 구현</summary>

&#x20;                                           ![](images/layout-practice-scroll.jpg)

catalog_home.sbml에서 object cell로&#x20;

**S_**_**INQUIRE_cell의**_ JS(context)가 적용되어지는 독립적인 layout을 구현합니다.

#### sbml

```

=object section: section=sell_detail, width=1pw, height=0.93ph
=object cell: display-unit="S_INQUIRE", \
width=1pw, height=0.07ph, position=abs, gravity="bottom"

=begin catalog: id=sell_detail, display=none
...
=end catalog

```

#### tip

* object cell은 파일이름 규칙에 따라 파일의 끝명이 '_cell'의 파일들을 탐색합니다.
* 따라서 display-unit에 S_INQUIRE_cell.* 의 'S_INQUIRE'로 연결합니다.
* object cell의 width는 object section과 마찬가지로 1pw이며, height는 object section의 높이를 제외하여 0.07ph 입니다.
* object cell을 화면의 하단에 고정시켜야 하므로, position=abs, gravity=bottom을 적용시킵니다.





</details>

# 복습하기

_1. abs 포지션 , display=block의 내용이 전달되어지지 않은 것 같아 해당 내용 다시 복습_

_2. catalog_home.sbml에서 object cell을 bottom에 fixed는 방법_

### Object Cell에서 세 개의 object 정렬

권장되는 방법으로는 오른쪽, 왼쪽 정렬에 따른 하위 섹션(=begin left .. =end left / =begin right … end right)을 만든 후, 하위 섹션에 사용되는 오브젝트를 넣는 것입니다.

<figure><img src="images/image (4).png" alt=""><figcaption></figcaption></figure>

```javascript
// S_BOTTOM_cell.sbml : 적용된 스타일을 바로 알기 위해 sbml에 스타일 적용
=begin cell

=begin left: display=block, position=abs, gravity=left, x=20
=object image: width=
=end left

=begin right: display=block, position=abs, gravity=right, x=-20, text-align=right
=(object button: margin-right=10dp,... )= =(object button: margin-left=20dp, ...)=
=end right

=end cell
```

object는 기본적으로 block 속성입니다. 섹션을 오브젝트와 같이 block 속성을 가지도록 하기 위해서 'display=block' 해야 합니다.

gravity를 left 또는 right로 설정하게 될 경우, 위아래 간격이 맞춰지면서 가운데 정렬로 왼쪽 혹은 오른쪽으로 배치됩니다.

postion=abs이므로, 'x='를 이용해서 view 양 끝단 간격을 조정합니다. (또는 padding-right or padding-left 사용 → margin은 적용되지 않는다.)

right 섹션에서 inline으로 두 개의 button에 간격을 만들기 위해서는 속성에 margin-left, margin-right를 적용합니다.

{% hint style="info" %}
margin-collapse

margin-collapse는 margin이 겹치는 부분 중 더 큰 값을 가진 것이 적용됩니다.
{% endhint %}

| 구분        | margin-left | margin-left | total |
| --------- | ----------- | ----------- | ----- |
| jamkit    | 10          | 20          | 20    |
| html, css | 10          | 20          | 30    |

* 기존의 css, html 방식대로라면 두 개의 margin이 합쳐져 30입니다.
* jamkit에서는 margin-collapse가 일어나 horizontal의 total margin은 20입니다.
* margin-left가 margin-right보다 절대값이 더 큰 것을 확인할 수 있습니다.

<figure><img src="images/image (32).png" alt=""><figcaption></figcaption></figure>

### Object cell을 bottom에 Fixed 처리

스크롤과 함께 한 파일 내에서 처리하는 방법에 대하여 설명합니다.

스크롤의 경우, 로드된 화면의 1pw, 1ph에 맞춰 생성됩집니다.

따라서 아래의 코드와 같이 object cell을 적용할 경우 스크롤을 내리면서 object cell의 view가 fixed되지 않고 화면에서 움직이는 것을 확인할 수 있습니다.

```javascript
// catalog_home.sbml

=object cell: position=abs, gravity=bottom
```

따라서 object section과 object cell을 이용해 두 개의 영역으로 분리하여야 합니다.

<figure><img src="images/image (14).png" alt=""><figcaption></figcaption></figure>

object cell을 제외한 구현 view의 경우 '=begin catalog … =end catalog' 내에 구현되었기 때문에 catalog 섹션에 id를 부여해 이를 obejct section의 section과 연결하는 것입니다.

obejct section에 view를 연결할 때 주의점으로는 height 입니다. height의 경우 object cell의 height를 함께 계산해야 합니다.

height=1ph로 할 경우, 스크롤로 가장 하단으로 내릴 시 하단에서 보여야 할 파트가 object cell에 의해서 보이지 않는 문제점을 발견할 수 있습니다.

따라서 object section의 height=0.9ph, object cell의 height=0.1ph와 같이 설정하여야 합니다.

```javascript
=object section: section=carrot, width=1pw, height=0.9ph
=object cell: display-unit="S_INQUIRE", width=1pw, height=0.1ph, position=abs, gravity=bottom

=begin catalog: id=carrot, display=none
...
=end catalog
```
