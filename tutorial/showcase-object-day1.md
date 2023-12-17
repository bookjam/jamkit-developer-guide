# 쇼케이스 오브젝트 Day 1

### jamkit 엔진 동작

catalog\_main의 경우, 자동으로 jamkit 엔진에 view를 만들어 sbml, sbss를 올리라는 명령이 들어갑니다.

이때 엔진은 특정한 데이터를 만듭니다. (데이터는 key, value가 쌍으로 이루어집니다.)

이 데이터를 파일 이름 규칙에 따라 sbml을 찾고 결합시킨 후, 데이터를 뿌립니다.

sbml에서 ’$’를 이용해 아래의 그림과 같이 (특정 or 전체) 데이터를 요청할 경우, 해당 sbml에서 요청하는 데이터를 찾은 후, sbml 내 요청 부문과 일치하는 데이터로 replace하여 sbml을 만든 후, 화면이 올라갑니다.

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

### showcase object

container object는 특정한 sbml, sbss를 영역 내 형태에 맞는 것을 찾아서 뿌려줄 수 있는 것입니다. 대표적인 것으로 showcase이며, 다루기 가장 어려운 container object입니다.

showcase의 경우 data가 없으면 사용할 수가 없습니다. 즉, data가 있어야 사용할 수 있는 object입니다.

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

#### cell의 갯수

showcase에서 가장 중요한 것은 column-count, row-count입니다. 한 화면에 몇 개의 셀을 보여줄지 결정하는 속성으로, 위의 두 속성에 따라 vertical, horizontal 무한 스크롤 배치가 가능한 것입니다.

* column-count : vertical\
  예시1) column-count=1 : 아래 그림의 <1>번\
  row-count는 지정하지 않아야 데이터의 수만큼 뿌려집니다\
  \
  예시2) column-count=2 : 아래 그림의 <2>번\
  row-count는 지정하지 않아야 데이터의 수만큼 뿌려집니다\

* row-count: horizontal\
  예시3) column-count=1, row-count=4 : 아래 그림의 <3>번\
  1개의 column에 4개의 row만큼만 뿌려지며, 데이터가 5개 이상일 경우, 우측으로 스크롤됩니다.\
  \
  예시4) row-count=1: 아래 그림의 <4>번\
  column-count는 지정하지 않아야 데이터의 수만큼 뿌려집니다

<figure><img src="../.gitbook/assets/image (12) (1).png" alt=""><figcaption></figcaption></figure>

#### cell의 크기

showcase 내의 cell 크기는 cell-size를 이용해서 조정할 수 있습니다. cell-size가 object showcase보다 클 경우, 스크롤이 자동 적용됩니다.

```javascript
cell-size="[width] [height]"

//tip
cell-size="0 200dp"
-> width가 0이라는 것은 object showcase의 width에 맞춰 cell의 width가 자동으로 조정되는 것입니다.
```

#### cell의 간격

showcase 내의 cell 간격은 cell-spacing를 이용하면 됩니다.

```javascript
cell-spacing=40dp
```

#### showcase에 데이터 넣는 방법

다양한 방법이 있지만, 내부 데이터베이스인 sqlite의 특정한 데이터 집합을 showcase가 읽어 cell로 구성하는 방법으로 설명합니다.

object showcase에서 name은 ‘showcase\_…\_cell.sbml’ 파일을 연결하는 설정입니다.

object cell에서와 마찬가지로 파일 이름 규칙을 기반으로 sbml,sbss 파일을 연결합니다.

#### name에 설정된 값의 연결 동작(jamkit 엔진 동작)

{% code overflow="wrap" %}
```javascript
// catalog_home.sbml
=object showcase: name=balance, width=0.9pw, height=0.9ph, cell-size="0 30dp", cell-spacing=10dp

// showcase_balance_cell.sbml
=begin cell
=object label: text="balance ${title}"
=end cell
```
{% endcode %}

* data 찾기\
  sqlite의 showcases 테이블에서 showcase가 balance인 데이터를 찾습니다.

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

*   파일 찾기

    파일 이름 규칙에 따라 showcase\_balance\_cell.sbml을 찾습니다.
* 파일 내 데이터 결합시켜 sbml 올리기\
  showcase\_balance\_cell.sbml 파일에서 지정한 데이터 요청 구문`(${YEAR})`과 맞는 데이터를 매핑시켜 sbml을 만들고 이를 화면에 올립니다.

⇒ 따라서 object showcase에 연결되는 sbml의 파일명 시작은 'showcase\_'가 되어야 하며, showcase 내의 구현되는 cell이기에 파일명 끝은 '\_cell'이 되어야 합니다.
