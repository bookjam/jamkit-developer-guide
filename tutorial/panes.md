# 오브젝트 연결, panes 오브젝트

### 오브젝트 간 연결하기

오브젝트의 액션이나 상태에 따라 다른 오브젝트에 변화를 주기 위해서는 오브젝트간 연결이 필요합니다.

#### cell을 선택했을 때, 다른 cell에 변화 주기

우선, cell의 상태에 대해서 알아야 하는데 cell의 상태는 normal, selected, focused 세 가지가 있습니다.

"selected"는 편집 모드에서 cell을 선택했을 때 가지는 상태값입니다.

"focused"는 유저가 cell을 탭한 상태로, 이 상태값은 $STATE == "focused"로서, 이 값은 cell 오브젝트에만 전달할 수 있습니다. 예를 들어, showcase의 어떤 cell을 탭했을 때, header의 값을 바꾸는 것입니다.

* 원본 오브젝트에 id를, 대상 오브젝트에 owner를 부여해야 합니다. 이때, id와 owner는 같아야 합니다.
* 원본 오브젝트에는 selectable=yes, 대상 오브젝트에는 type=slave 속성이 필요합니다.

```javascript
// 원본 오브젝트: 유저가 cell을 탭하는 오브젝트
=object showcase: id=showcase1, selectable=yes

// 대상 오브젝트: 유저의 동작에 따른 상태값을 받아서 변하는 오브젝트
=object cell: owner=showcase1, type=slave
```

#### showcase가 스크롤할 때, 자기 위치를 바꾸는 동작

showcase를 스크롤할 때, 특정 cell이 따라서 움직이도록 하는 동작을 구현해보겠습니다.

* 원본 오브젝트에 id를, 대상 오브젝트에 owner를 부여해야 합니다. 이때, id와 owner는 같아야 합니다.
* 대상 오브젝트에는 follows-scroll=yes 속성이 필요합니다.
* 대상 오브젝트가 최대로 움직일 수 있는 좌표를 지정할 수 있습니다. showcase의 스크롤 방향에 따라 y(상하 스크롤), x(좌우 스크롤) 좌표를 지정합니다.&#x20;
  * min-x: 최대로 좌측으로 움직일 수 있는 x 좌표
  * max-x: 최대로 우측으로 움직일 수 있는 x 좌표
  * min-y: 최대로 올라갈 수 있는 y 좌표
  * max-y: 최대로 내려갈 수 있는 y 좌표
* 대상 오브젝트가 움직이는 속도를 지정할 수 있습니다.
  * velocity-when-follow

{% code overflow="wrap" %}
```javascript
// 원본 오브젝트: 유저가 스크롤하는 오브젝트
=object showcase: id=showcase1

// 대상 오브젝트: 유저의 동작에 따른 상태값을 받아서 변하는 오브젝트
=object cell: owner=showcase1, follows-scroll=yes, \
                verlocity-when-follow=0.1, \
                min-y=0.1ph, max-y=0
```
{% endcode %}

### panes 오브젝트

panes 오브젝트는 showcase 오브젝트를 가로나 세로로 여러 개 진열하는 오브젝트입니다. 화면을 좌우로 스와이프하면 통째로 화면이 전환됩니다.

#### navibar

상단에 navibar를 배치하여 탭으로 이동할 수도 있습니다. panes\_{name}\_navibar\_cell.sbml/sbss로 구성된 파일이 필요합니다.

<table><thead><tr><th width="225">속성</th><th>설명</th></tr></thead><tbody><tr><td>has-navibar</td><td><strong>navibar 사용 여부 설정</strong><br>💡 default 값 has-navibar=no</td></tr><tr><td>navibar-cell-size</td><td><strong>navibar cell의 크기 설정</strong><br>"[가로] [세로]"<br>💡 has-navibar=yes 설정 필요</td></tr><tr><td>navibar-cell-spacing</td><td><strong>navibar cell 사이의 간격</strong><br>💡 has-navibar=yes 설정 필요</td></tr><tr><td>navibar-margin</td><td><strong>navibar 전체를 감싼 영역의 margin</strong><br>💡 has-navibar=yes 설정 필요</td></tr><tr><td>navibar-center-align</td><td><strong>navibar 전체를 center로 정렬 여부</strong><br>💡 default 값 navibar-center-align=no<br>💡 has-navibar=yes 설정 필요</td></tr><tr><td>navibar-position</td><td><strong>navibar의 위치 설정 { top, left, bottom, right 등}</strong><br>💡 default 값 navibar-position=bottom<br>💡 has-navibar=yes 설정 필요</td></tr></tbody></table>

```javascript
// SBML
=object pane: name=home, has-navibar=yes, navibar-cell-size="100dp 60dp", \
             navibar-cell-spacing=5dp, navibar-margin="10dp", \
             navibar-center-align=yes, \
             navibar-position=bottom
```

#### 환경변수를 통한 모양 바꾸기

sbss 파일에 $STATE == "selected" 옵션을 준다.

```javascript
// sbss
if $STATE == "selected"
    #label_title: text-color=#0f0
end
```

