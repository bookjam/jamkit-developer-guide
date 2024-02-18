# 쇼케이스 오브젝트 Day 2

### 파일 이름 규칙 우선 순위

지금까지는 showcase name을 통해 data와 sbml, sbss파일을 찾아낸 후 화면이 만들어졌지만, 아래의 우선 순위로 파일을 탐색합니다.

순위에 따른 연결 sbml, sbss을 탐색한 후, 해당 sbml, sbss이 없을 경우 다음 순위의 파일들을 탐색합니다.

{% hint style="info" %}
* **id - 특정 id를 지정하는 경우(has-own-sbml=yes로 설정되어야 함)**
  id : S_MY_PRACTICE3_000001
  <mark style="color:red;">S_MY_PRACTICE3_000001</mark>_cell.sbml/sbss를 찾는다
* **template - 템플릿을 지정하는 경우**
  name: practice3
  template: installed
  showcase_<mark style="color:red;">practice3</mark>_<mark style="color:red;">installed</mark>_cell.sbml/sbss를 찾는다
* **name - 쇼케이스 이름을 지정하는 경우**
  name: practice3
  showcase_<mark style="color:red;">practice3</mark>_cell.sbml/sbss를 찾는다
* **defaut - 아무것도 지정하지 않은 경우**
  showcase_<mark style="color:red;">default</mark>_cell.sbml/sbss를 찾는다
{% endhint %}

### data-script를 통한 데이터 연결

showcase object 첫 번째 강의에서 showcase object의 경우 data가 없으면 동작할 수 없다고 설명하였습니다.

지금까지는 sqlite의 data 연결로만 설명을 하였습니다.

데이터는 스크립트를 이용해서 넣을 수도 있습니다.

스크립트에서 데이터를 만들어(api로 데이터 받는 경우 혹은 테스트용 하드로 제작하는 경우 등) object showcase에 data-script로 해당 스크립트를 연결하면 됩니다.

```javascript
//catalog_home.sbml
=object showcase: data-sctipt="feed_apps"
```

<figure><img src="images/image (3).png" alt=""><figcaption></figcaption></figure>

showcase name을 이용해 데이터를 받았던 것을 data-script를 통해서 데이터를 넣었으므로, 화면(sbml, sbss) 연결 설정이 필요합니다.

이때 사용되는 설정이 alternate-name입니다. alternate-name을 이용하여 화면으로 나타낼 특정 sbml과 sbss 파일을 연결할 수 있습니다.

```javascript
//catalog_home.sbml
=object showcase: data-script="feed_apps", \  //데이터 연결
                  alternate-name="apps", \    //화면(sbml,sbss) 연결
                  style="showcase_list"       //스타일 연결
```

<figure><img src="images/image (9).png" alt=""><figcaption></figcaption></figure>

### sqlite와 data-script 비교

showcase에서 구현되는 cell의 layout을 구성하는 showcase_apps_cell에 대하여 설명합니다. 간단하게 title만 나타낼 것이기 때문에 복잡한 구성은 하지 않았습니다.

<figure><img src="images/image (33).png" alt=""><figcaption></figcaption></figure>

간단하게 구현되는 코드지만 이 챕터를 넣은 이유는 catalog_home에서 data-script로 js 내에서 api로 받은 데이터를 연결하였을 때와 파일 이름 규칙(sqlite)으로 데이터 연결하는 name을 비교하기 위해서입니다.

data 중 title의 value로 비교를 진행하기에, 각 value를 다르게 하였습니다.

#### data-script

해커뉴스 open api 이용

```javascript
=object showcase: data-script="feed_apps", 
alternate-name="apps"
```

<figure><img src="images/image (26).png" alt=""><figcaption></figcaption></figure>

<figure><img src="images/image (8).png" alt=""><figcaption></figcaption></figure>

#### sqlite

```javascript
=object showcase: name="balance2", alternate-name="apps"
```

<figure><img src="images/image (30).png" alt=""><figcaption></figcaption></figure>

<figure><img src="images/image (36).png" alt=""><figcaption></figcaption></figure>

sqlite로 data를 연결한 예시를 살펴보면, showcase object 강의 내용 1과 같이 name을 사용한 것을 볼 수 있습니다.

data는 name을 통해 가져왔지만, alternate-name을 사용해 특정 연결 sbml을 지정하였기에, name으로 파일 이름 규칙이 적용된 showcase_balanace2_cell.sbml로 연결되지 않았습니다.

만약 아래의 코드와 같이 name만 사용하였다면, 이전 강의에서 설명하였던 대로 showcase_balance2_cell.sbml을 탐색한 후, showcase_balance2_cell.sbss의 layout이 적용됩니다.

### transient_cell : 데이터 화면 렌더링 전 적용 화면

위의 showcase_apps_cell까지 진행하다 보면 아래의 에러가 계속 발생합니다.

<figure><img src="images/image (35).png" alt=""><figcaption></figcaption></figure>

showcase object는 data가 있어야 사용할 수 있음을 지난 강의에서 설명했습니다.

data를 불러오는 동안 sbml 파일의 화면 렌더링 또한 늦습니다. 이렇게 시간이 1초 이상 소요되어 화면에 렌더링되기 전에 사용하는 화면이 transient_cell입니다.

<figure><img src="images/image (7).png" alt=""><figcaption></figcaption></figure>

가장 처음 설명한던 파일 이름 우선 적용 규칙을 떠올려 보시면, showcase_default_transient_cell은 우선 순위의 설정 파일들이 모두 없는 경우, 가장 마지막에 탐색되는 파일입니다.

이 default_transient 파일을 찾지 못하였다는 에러를 통해서 data가 연결되는 sbml, sbss뿐만 아니라 transient 관련 sbml, sbss도 같이 탐색됨을 알 수 있습니다.

{% hint style="info" %}
* **ID를 지정한 경우**
  =object showcase: id="S_TEST_01"
  <mark style="color:red;">S_TEST_01</mark>_transient_cell.sbml/sbss를 탐색
* **showcase name을 지정한 경우**
  =object showcase: name="test"
  showcase_<mark style="color:red;">test</mark>_transient_cell.sbml/sbss를 탐색
* **showcase의 alternate name을 지정한 경우**
  =object showcase: name="test", alternate-name="apps" showcase_<mark style="color:red;">apps</mark>_transient_cell.sbml/sbss를 탐색
{% endhint %}

#### 예시

* transient 파일 생성
  showcase_{name}_transient_cell.sbml/sbss 두 개의 파일을 생성합니다.
* transient sbml 완성
  showcase_{name}_cell의 레이아웃에 맞게 showcase_{name}_trasient_cell을 완성합니다.

<figure><img src="images/image (27).png" alt=""><figcaption></figcaption></figure>

위의 작업을 완료한 후, 결과 화면은 아래 이미지와 같습니다. 스크롤로 다음 데이터 연결 화면을 렌더링하기 전, 적용되는 transient 화면입니다.

<figure><img src="images/image (17).png" alt=""><figcaption></figcaption></figure>

### object showcase의 다양한 property

앞서 설명한 transient cell은는 스크롤로 데이터를 새로 불러서 화면에 렌더링할 때 적용됩니다. object showcase에 설정되는 필수 설정 외에 추가적인 설정을 설명합니다. 이러한 설정이 없어도 transient cell이 적용되지만 트래픽 및 메모리를 고려해야 할 때 아래의 설정을 적절하게 이용할 수 있기 때문입니다.

<table><thead><tr><th width="225">Property</th><th width="80">value</th><th>Description</th></tr></thead><tbody><tr><td>preload-count</td><td>숫자</td><td>object showcase의 배치될 cell의 수보다 크게 하여, 미리 일부 데이터를 화면에서 받아놓는 설정입니다.</td></tr><tr><td>keep-count</td><td>숫자</td><td>새로운 데이터를 받을 때, 이전의 데이터는 메모리 최적화를 위해서 사라집니다. 가장 최근의 데이터를 기점으로 n개의 데이터를 유지하는 설정입니다.</td></tr><tr><td>keeps-offscreen-cells</td><td>yes</td><td>스크롤하며 새로운 데이터를 받더라도 이전의 모든 데이터가 유지되도록 하는 설정입니다.</td></tr><tr><td>reloads-when-pull</td><td>yes</td><td>화면을 아래로 끌어 '새로고침'하는 설정입니다.</td></tr><tr><td>eager-loading</td><td>yes</td><td>첫 로딩 시, 모든 데이터를 받아 놓는 설정입니다.</td></tr><tr><td>max-cell-count</td><td>숫자</td><td>스크롤이 적용되지 않도록 일부 데이터만 보여지는 설정입니다.</td></tr><tr><td>first-cell</td><td>숫자</td><td>cell마다 고유의 index가 있는데 해당 index가 가장 상단으로 위치하도록 지정하는 설정입니다.</td></tr></tbody></table>

#### 예시 코드 내, object showcase에 적용된 설정

```javascript
//catalog_home.sbml
=object showcase: data-script="feed_apps", \
                alternate-name="apps", style="showcase_list"

//catalog_home.sbss
#showcase_list: width=0.9pw, height=0.9ph, \
                content-background-color=#36B19CF6, \

                column-count=1, \
                cell-size="0 100dp", cell-spacing=10dp, \
                
preload-count=10, keep-count=10, \
                reloads-when-pull=yes, \
                
content-margin="50dp 10dp"
```

* preload-count
  첫 로딩 시, object showcase에서 보여지는 cell의 데이터 외에 10개의 데이터를 미리 받아 놓는 설정입니다.

```javascript
=object showcase: preload-count=10
```

* keep-count
  기본적으로 object showcase에서 사용자에게 보이는 데이터 외에는 메모리 최적화를 위해서 삭제됩니다. 이전의 데이터를 일부 유지하고 싶은 경우 keep-count 설정을 통해 유지할 수 있습니다.

```javascript
=object showcase: keep-count=10
```

* keeps-offscreen-cells=yes
  (무한) 스크롤로 새 데이터를 불러와도 이전에 load된 모든 데이터는 삭제되지 않고 계속 유지됩니다.

```javascript
=object showcase: keeps-offscreen-cells=yes
```

* reloads-when-pull=yes
  view 전체를 아래로 끌어내릴 경우, reload될 수 있게 설정하는 것입니다. android의 경우에서는 위의 설정으로도 적용되지만, iOS의 경우에서는 해당 설정이 적용될 수 있는 sbml, sbss 파일을 추가해야 합니다.

```javascript
=object showcase: reload-when-cell=yes
```

* eager-loading
  모든 데이터를 첫 로딩 시 한번에 받아오는 설정입니다.

```javascript
=object showcase: eager-loading=yes
```

* max-cell-count
  일반적으로 object showcase는 데이터 개수 만큼 무한 스크롤이 적용됩니다. max-cell-count를 설정하면 해당 설정 수만큼만 화면에 나타나며, 스크롤이 적용되지 않습니다. 주로 max-cell-count 설정은 메인 페이지에서 간단하게 보여주는 순위 component입니다. '더보기'와 같은 버튼 클릭으로 페이지 이동을 유도합니다.

```javascript
=object showcase: max-cell-count=3
```

<figure><img src="images/image (6).png" alt=""><figcaption></figcaption></figure>

* first-cell
  first-cell을 사용해서 특정 cell의 index를 지정할 경우 해당 인덱스가 가장 상단에 배치됩니다.

```javascript
=object showcase: firtst-cell=3
```

<figure><img src="images/image (28).png" alt=""><figcaption></figcaption></figure>

### empty cell: 검색 결과에 데이터가 없을 때 화면

데이터가 없는 경우에는 showcase_{name}_empty.cell을 이용합니다. empty_cell은는 데이터 연결 화면이 렌더링, transient 적용 전에 구현되므로 loading용으로도 사용할 수 있습니다. 또한 데이터 연결 화면에서 해당 데이터가 없는 경우 나타내는 화면으로 사용할 수 있습니다.

파일 이름 규칙이 또한 적용되며, 해당 파일이 없어도 문제되지 않습니다. data-script로 연결 예시에서 API 주소를 변경하여 empty 파일이 적용되는 예시를 통해서 확인하면 아래와 같습니다.

* emtpy 파일 생성
  &#x20;프로젝트 구조에서와 같이 showcase_apps_empty.sbml과 showcase_apps_empty.sbss 두 개의 파일을 생성합니다.
* showcase_apps_empty.sbml 완성
  아래의 이미지와 같이 sbml에서는 데이터 연결이 없습니다.
* data-script, API 끊기
  catalog_home.js에서 data-script에 연결된 function 내 API 연결 주소에 '!'를 추가하여, 불러오는 데이터가 없도록 합니다.

<figure><img src="images/image (31).png" alt=""><figcaption></figcaption></figure>

<figure><img src="images/image (20).png" alt=""><figcaption></figcaption></figure>

위의 작업을 완료한 후, 결과 화면은 아래의 이미지와 같습니다. catalog_home에서 object showcase에 설정한 width와 height는 유지되지만 showcase_apps_empty의 object label이 화면의 결과로 나오는 것을 확인할 수 있습니다.

<figure><img src="images/image (1).png" alt=""><figcaption></figcaption></figure>

# 실습하기

### 아래의 화면을 구현해보세요

<figure><img src="images/image (18).png" alt=""><figcaption></figcaption></figure>

### 실습 가이드

#### 개요

* 섹션 속성은 [basic-style.md](../../reference/basic-style.md "mention") 또는 [이 문서](https://bookjam.github.io/jamkit/refs_styles/)를 참고하세요.
* 오브젝트 속성은 [basic-object.md](../../reference/basic-object.md "mention") 또는 [이 문서](https://bookjam.github.io/jamkit/refs_objects/)를 참고하세요.
* jamkit으로 "practice" 프로젝트를 생성하고, cataog_home.sbml과 sbss의 본문을 지우고 작업하세요.
* 필요한 이미지는 [이 파일](https://bpmgbiz.sharepoint.com/:f:/s/BPMG_Lecture/El6A41a0bpVLnzI8VhqMjMsBzAnAYA8WMwVTa8Oa9TNcFg?e=50fEuE)을 다운로드하세요.
* 디바이스나 emulator를 실행하여 직접 화면을 보면서 작업하세요.
* label, textfield, button 등의 오브젝트는 width, height 둘 다 반드시 지정해야 구현됩니다.

#### **작업 순서**

{% hint style="info" %}
catalog_home.sbml에서 catalog 섹션 내에서 아래의 섹션들을 구현합니다.
{% endhint %}

* catalog_home.sbml
  *
*

### 최종 결과 파일

* 이 [폴더](https://bpmgbiz.sharepoint.com/:f:/s/BPMG_Lecture/EtAHBp7Yo_5EiIpOtQl8SnwBIsvMsxewI5k8LtFu3LjUMA?e=2IMBs6)의 [쇼케이스 오브젝트 Day 2_실습하기.zip](https://bpmgbiz.sharepoint.com/:u:/s/BPMG_Lecture/EXofNF2m8G1JjXiFEHJCQ-ABwUlGs60W0WfnaOmLB9qj4Q?e=a10xf5)을 다운로드해서 확인해보세요.

### 구현 가이드

