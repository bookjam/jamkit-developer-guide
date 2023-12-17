# 복습하기

_1. abs 포지션 , display=block의 내용이 전달되어지지 않은 것 같아 해당 내용 다시 복습_

_2. catalog\_home.sbml에서 object cell을 bottom에 fixed는 방법_

### Object Cell에서 세 개의 object 정렬

권장되는 방법으로는 오른쪽, 왼쪽 정렬에 따른 하위 섹션(=begin left .. =end left / =begin right … end right)을 만든 후, 하위 섹션에 사용되는 오브젝트를 넣는 것입니다.

<figure><img src="../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>

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

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

### Object cell을 bottom에 Fixed 처리

스크롤과 함께 한 파일 내에서 처리하는 방법에 대하여 설명합니다.

스크롤의 경우, 로드된 화면의 1pw, 1ph에 맞춰 생성됩집니다.

따라서 아래의 코드와 같이 object cell을 적용할 경우 스크롤을 내리면서 object cell의 view가 fixed되지 않고 화면에서 움직이는 것을 확인할 수 있습니다.

```javascript
// catalog_home.sbml
=object cell: position=abs, gravity=bottom
```

따라서 object section과 object cell을 이용해 두 개의 영역으로 분리하여야 합니다.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

object cell을 제외한 구현 view의 경우 '=begin catalog … =end catalog' 내에 구현되었기 때문에 catalog 섹션에 id를 부여해 이를 obejct section의 section과 연결하는 것입니다.

obejct section에 view를 연결할 때 주의점으로는 height 입니다. height의 경우 object cell의 height를 함께 계산해야 합니다.

height=1ph로 할 경우, 스크롤로 가장 하단으로 내릴 시 하단에서 보여야 할 파트가 object cell에 의해서 보이지 않는 문제점을 발견할 수 있습니다.

따라서 object section의 height=0.9ph, object cell의 height=0.1ph와 같이 설정하여야 합니다.

{% code overflow="wrap" %}
```javascript
=object section: section=carrot, width=1pw, height=0.9ph
=object cell: display-unit="S_INQUIRE", width=1pw, height=0.1ph, position=abs, gravity=bottom

=begin catalog: id=carrot, display=none
...
=end catalog
```
{% endcode %}
