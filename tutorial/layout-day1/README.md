# 레이아웃 다루기 Day 1

### VIEW

* Jamkit의 화면은 view라고 부르며, 각 영역별로 구분된 컴포넌트 구조다.
* view 안에 view가 있을 수 있다.
* 특정한 view는 동일한 파일명의 sbml, sbss, js 파일로 구성되어 있다.

### SBML과 SBSS

#### SBML: 표현하려는 내용이 들어있는 파일로서 section과 object로 구성되어 있다.

* section은 begin으로 시작하여 end로 끝난다.
* section에는 반드시 이름이 필요하다(end에서는 생략할 수 있다).

```javascript
// SBML
=begin text
표현하려는 내용이 들어갑니다.
=end text // 'text'는 생략 가능
```

#### SBSS: section과 object의 모양을 규정하는 파일로서 section 경로와 스타일(#)로 구성되어 있다.

* section 경로
  *
* 스타일
  * 주로 object에 적용하는 경우가 많다.
  * 자주 쓰이는 색상이나 모양 등을 스타일로 지정하여, section 경로나 다른 스타일에 적용할 수 있다.

```javascript
// SBSS
#blue: text-color=#00F

/catalog: page-background-color=#ff0, style=blue
```

### SECTION과 OBJECT

* section에는 텍스트, 하위 section, object가 들어갈 수 있다.
* object는 특정한 기능을 수행하는 block 형태의 개체다.

```javascript
// SBML
=begin book

=begin title
여기는 타이틀 영역입니다.
=begin title

=begin body
여기는 본문 영역입니다.
=end body

=object photo: filename=photo1.jpg, style= photo
=object button: style=button

=end book

// SBSS
#photo: width=0.3pw, align=center
#button: label-color=#00F

/book: page-background-color=#FFF
/book/title: font-size=2, text-color=#F00
/book/body: font-size=1.5
```

### inline 스타일

* line 내에서 별개의 스타일을 지정할 때, inline 스타일을 사용할 수 있다.
* sbss에서 지정한 스타일을 쓸 경우: =\[{스타일명}|스타일을 적용할 텍스트]=

```javascript
// SBML
여기부터는 =[blue|파란색]=입니다.

// SBSS
#blue: text-color=#00F
```

* sbml에 직접 스타일을 지정할 경우: =\[:적용할 스타일|스타일을 적용할 텍스트]=

```javascript
// SBML
여기부터는 =[:text-color=#00F|파란색]=입니다.
```

### inline 오브젝트

* line 내에 object를 삽입하고 싶을 때 사용한다.

```javascript
// SBML
=(object button: style=button)=

// SBSS
#button: width=20dp, height=30dp
```

### object sbml

* 내부에 sbml이 들어가는 오브젝트.
* sbml 내에서 특정 영역을 별도의 sbml처럼 처리할 때 쓴다.

### 크기 지정 단위

* px, dp: 해상도를 기준으로 한 단위, dp를 표준으로 사용한다
  * px: 일반적인 해상도 수, **화면 크기에 따라 다른은 크기로 구현된다**
  * dp: 1인치에 들어가는 픽셀의 갯수, **화면 크기와 상관없이 같은 크기로 구현된다**
* pw, ph: 전체 화면을 기준으로 한 단위
  * 전체 화면 가로 1pw
  * 전체 화면 세로 1ph



