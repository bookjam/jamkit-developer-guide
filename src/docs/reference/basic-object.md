# 기본 오브젝트

!!! note

    구글 스프레드시트는 [**여기**](https://docs.google.com/spreadsheets/d/1Wn2GCSGIPeWzNZKlR4Mbcr1NK-GTcJ7f3b5CVup9iLU/edit?usp=sharing)에서 확인하세요.

### 오브젝트 공통 <a href="#_1" id="_1"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 속성 <a href="#_2" id="_2"></a>

| 속성                       | 타입(허용값) | 기본값     | 단위                  | 설명                                                                     |
| ------------------------ | ------- | ------- | ------------------- | ---------------------------------------------------------------------- |
| id                       | String  | None    |                     | 오브젝트의 ID. 화면에 존재하는 오브젝트 중 유일한 값이어야 한다.                                 |
| group                    | String  | None    |                     | 오브젝트의 그룹 ID. 동일한 그룹 ID의 오브젝트들은 하나의 그룹으로 묶을 수 있다.                       |
| alpha                    | Float   | 1       |                     | 오브젝트의 알파값. 0일 경우 오브젝트가 투명해진다.                                          |
| hidden                   | Boolean | no      |                     | 오브젝트를 숨기려면 yes를 지정한다.                                                  |
| rotate                   | Float   | 0       |                     | 지정된 값만큼 오브젝트를 회전시킨다. 이 때의 단위는 radian이다. 즉, 180도를 회전시키려면 3.14를 지정하면 된다. |
| ignore-touches           | Boolean | no      |                     | 오브젝트가 터치 이벤트를 처리하지 않도록 하려면 yes를 지정한다.                                  |
| save-states              | Boolean | no      |                     | 오브젝트의 상태를 저장하려면 yes를 지정한다. 이 때, id도 지정되어 있어야 한다.                       |
| content-background-color | Color   | 투명      |                     | 콘텐츠 영역의 배경색.                                                           |
| content-border-width     | Float   | 0       | dp, em, layout의 상대값 | 콘텐츠 영역 보더의 굵기.                                                         |
| content-border-color     | Color   | #000000 |                     | 콘텐츠 영역 보더의 색상.                                                         |
| content-border-radius    | Float   | 0       | dp, em, layout의 상대값 | 콘텐츠 영역 보더의 곡면 크기.                                                      |
| hides-when-activate      | Boolean | no      |                     | 오브젝트가 활성화될 때 숨기려면 yes를 지정함.                                            |
| hides-when-pause         | Boolean | no      |                     | 오브젝트가 일시정지할 때 숨기려면 yes를 지정함.                                           |

#### 액션 <a href="#_3" id="_3"></a>

N/A

#### 이벤트 <a href="#_4" id="_4"></a>

| 이벤트 액션명                | 설명                 |
| ---------------------- | ------------------ |
| action-when-activate   | 오브젝트가 활성화될 때 발생함.  |
| action-when-deactivate | 오브젝트가 정지할 때 발생함.   |
| action-when-pause      | 오브젝트가 일시정지할 때 발생함. |
| action-when-resume     | 오브젝트가 재활성화될 때 발생함. |

### 이미지 (Image) <a href="#image" id="image"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_5" id="_5"></a>

```
=object image: filename="image.jpg"
```

#### 속성 <a href="#_6" id="_6"></a>

| 속성                 | 타입(허용값)                                                                                  | 기본값    | 단위 | 설명                                                                                         |
| ------------------ | ---------------------------------------------------------------------------------------- | ------ | -- | ------------------------------------------------------------------------------------------ |
| filename           | 파일명                                                                                      | None   |    | 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                                        |
| image-url          | URL                                                                                      | None   |    | 이미지의 URL. URL로 부터 이미지를 다운로드한다. 이 때, image-downloadable을 yes로 설정해야 한다.                      |
| mask-image         | 파일명                                                                                      | None   |    | 이미지 위에 겹쳐지는 마스크 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다. 마스크 이미지는 정가운데 한점을 중심으로 9-patch로 표현된다. |
| default-image      | 파일명                                                                                      | None   |    | 이미지가 아직 로드되어 있지 않을 때 나타낼 기본 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                           |
| image-downloadable | Boolean                                                                                  | no     |    | 이미지를 외부에서 다운로드할 수 있을 때 yes로 지정한다. 마스크 이미지와 기본 이미지는 다운로드 할 수 없다.                            |
| scale-mode         | fill / fit                                                                               | fit    |    | 이미지가 오브젝트의 크기에 맞지 않을 경우에 사용될 확대/축소 모드.                                                     |
| content-gravity    | left-top / left-bottom / right-top / right-bottom / top / right / bottom / left / center | center |    | 이미지가 확대/축소되어 표현되었을 때, 화면에 나타날 이미지 내의 위치를 지정한다.                                             |

#### 액션 <a href="#_7" id="_7"></a>

N/A

#### 이벤트 <a href="#_8" id="_8"></a>

N/A

### 포토 (Photo) <a href="#photo" id="photo"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_9" id="_9"></a>

```
=object photo: filename="photo.jpg"
```

#### 속성 <a href="#_10" id="_10"></a>

| 속성                       | 타입(허용값)                                                                                  | 기본값     | 단위                  | 설명                                                                                                  |
| ------------------------ | ---------------------------------------------------------------------------------------- | ------- | ------------------- | --------------------------------------------------------------------------------------------------- |
| filename                 | 파일명                                                                                      | None    |                     | 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                                                 |
| image-url                | URL                                                                                      | None    |                     | 이미지의 URL. URL로 부터 이미지를 다운로드한다. 이 때, image-downloadable을 yes로 설정해야 한다.                               |
| hidden-image             | 파일명                                                                                      | None    |                     | 뒤로 숨은 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다. dissolving이 yes인 경우, 0.4초 뒤에 이미지가 사라지고 뒤로 숨은 이미지가 드러난다.  |
| mask-image               | 파일명                                                                                      | None    |                     | 이미지 위에 겹쳐지는 마스크 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다. 마스크 이미지는 정가운데 한점을 중심으로 9-patch로 표현된다.          |
| default-image            | 파일명                                                                                      | None    |                     | 이미지가 아직 로드되어 있지 않을 때 나타낼 기본 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                    |
| image-downloadable       | Boolean                                                                                  | no      |                     | 이미지를 외부에서 다운로드할 수 있을 때 yes로 지정한다. 마스크 이미지와 기본 이미지는 다운로드 할 수 없다.                                     |
| scale-mode               | fill / fit                                                                               | fit     |                     | 이미지가 오브젝트의 크기에 맞지 않을 경우에 사용될 확대/축소 모드.                                                              |
| actual-mode              | Boolean                                                                                  | no      |                     | actual-mode를 yes로 지정하면 이미지가 오브젝트의 크기보다 작을 경우 scale-mode에 따라 이미지를 확대할 필요가 있을 때 이미지의 원본 크기보다 커질 수 없다. |
| content-gravity          | left-top / left-bottom / right-top / right-bottom / top / right / bottom / left / center | center  |                     | 이미지가 확대/축소되어 표현되었을 때, 화면에 보여질 이미지의 위치를 지정한다.                                                        |
| half-mode                | Boolean                                                                                  | no      |                     | 이미지를 반으로 나눠 절반 만을 표현하려면 yes로 설정한다. 표현될 이미지의 부분은 half-side로 지정할 수 있다.                                |
| half-side                | top / right / bottom / left / center                                                     | center  |                     | half-mode가 yes인 경우, 이미지가 표현될 부분의 위치를 지정한다                                                           |
| floating                 | Boolean                                                                                  | no      |                     | floating을 yes로 지정하면 이미지가 둥둥 떠다니는 애니메이션을 반복한다.                                                       |
| dissolving               | Boolean                                                                                  | no      |                     | dissolving을 yes로 지정하면, 오브젝트가 홀성화된지 0.4초 후에 뒤로 숨겨놓았던 이미지를 화면에 나타낸다.                                  |
| caption                  | String                                                                                   | None    |                     | 이미지의 캡션.                                                                                            |
| subcaption               | String                                                                                   | None    |                     | 이미지의 서브 캡션.                                                                                         |
| caption-font             | "\[weight] \[style] size family"                                                         |         |                     | 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"                          |
| caption-font-family      | serif / sans-serif / monospace / 글꼴 이름                                                   | serif   |                     | 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                                       |
| caption-font-size        | Float                                                                                    | 0.8     | em                  | 캡션의 글꼴 크기.                                                                                          |
| caption-font-weight      | normal / bold                                                                            | normal  |                     | 캡션의 글꼴 가중치.                                                                                         |
| caption-font-style       | normal / italic                                                                          | normal  |                     | 캡션의 글꼴 스타일.                                                                                         |
| caption-font-no-scale    | Boolean                                                                                  | no      |                     | 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                                                    |
| subcaption-font          | "\[weight] \[style] size family"                                                         |         |                     | 서브 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"                       |
| subcaption-font-family   | serif / sans-serif / monospace / 글꼴 이름                                                   | serif   |                     | 서브 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                                    |
| subcaption-font-size     | Float                                                                                    | 0.6     | em                  | 서브 캡션의 글꼴 크기.                                                                                       |
| subcaption-font-weight   | normal / bold                                                                            | normal  |                     | 서브 캡션의 글꼴 가중치.                                                                                      |
| subcaption-font-style    | normal / italic                                                                          | normal  |                     | 서브 캡션의 글꼴 스타일.                                                                                      |
| subcaption-font-no-scale | Boolean                                                                                  | no      |                     | 서브 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                                                 |
| caption-align            | left / right / center                                                                    | left    |                     | 캡션과 서브 캡션의 텍스트 정렬 방식.                                                                               |
| caption-height           | Float                                                                                    | 0       | dp, em, layout의 상대값 | 캡션 영역의 높이.                                                                                          |
| inner-caption            | Boolean                                                                                  | no      |                     | 캡션 영역을 이미지 영역 안으로 배치하려면 yes를 지정한다.                                                                  |
| caption-color            | Color                                                                                    | #000000 |                     | 캡션의 글자색.                                                                                            |
| subcaption-color         | Color                                                                                    | #000000 |                     | 서브 캡션의 글자색.                                                                                         |
| caption-background-color | Color                                                                                    | 투명      |                     | 캡션 영역의 배경색.                                                                                         |

#### 액션 <a href="#_11" id="_11"></a>

N/A

#### 이벤트 <a href="#_12" id="_12"></a>

N/A

### 포토플러스 (Photo Plus) <a href="#photo-plus" id="photo-plus"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_13" id="_13"></a>

```
=object photoplus: filename="photo.jpg"
```

#### 속성 <a href="#_14" id="_14"></a>

| 속성                       | 타입(허용값)                                                                                  | 기본값     | 단위                  | 설명                                                                            |
| ------------------------ | ---------------------------------------------------------------------------------------- | ------- | ------------------- | ----------------------------------------------------------------------------- |
| filename                 | 파일명                                                                                      | None    |                     | 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                           |
| image-url                | URL                                                                                      | None    |                     | 이미지의 URL. URL로 부터 이미지를 다운로드한다. 이 때, image-downloadable을 yes로 설정해야 한다.         |
| default-image            | 파일명                                                                                      | None    |                     | 이미지가 아직 로드되어 있지 않을 때 나타낼 기본 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.              |
| image-downloadable       | Boolean                                                                                  | no      |                     | 이미지를 외부에서 다운로드할 수 있을 때 yes로 지정한다. 기본 이미지는 다운로드 할 수 없다.                        |
| scale-mode               | fill / fit                                                                               | fill    |                     | 이미지가 오브젝트의 크기에 맞지 않을 경우에 사용될 확대/축소 모드.                                        |
| maximize-scale-mode      | fill / fit                                                                               | fit     |                     | 이미지가 전체화면으로 커졌을 경우에 사용될 확대/축소 모드.                                             |
| content-gravity          | left-top / left-bottom / right-top / right-bottom / top / right / bottom / left / center | center  |                     | 이미지가 확대/축소되어 표현되었을 때, 화면에 보여질 이미지의 위치를 지정한다.                                  |
| half-mode                | Boolean                                                                                  | no      |                     | 이미지를 반으로 나눠 절반 만을 표현하려면 yes로 설정한다. 표현될 이미지의 부분은 half-side로 지정할 수 있다.          |
| half-side                | top / right / bottom / left / center                                                     | center  |                     | half-mode가 yes인 경우, 이미지가 표현될 부분의 위치를 지정한다.                                    |
| shadow-color             | Color                                                                                    | #000000 |                     | 이미지 그림자 효과에 사용될 색상.                                                           |
| dim-color                | Color                                                                                    | #ffffff |                     | 이미지가 전체화면으로 커졌을 경우 이미지 주변 배경에 사용될 색상.                                         |
| photo-hidden             | Boolean                                                                                  | no      |                     | photo-hidden을 yes로 지정하면 이미지를 표시하지 않는다. 전체화면으로 커져야 하는 경우에는 무시된다.               |
| caption                  | String                                                                                   | None    |                     | 이미지의 캡션.                                                                      |
| subcaption               | String                                                                                   | None    |                     | 이미지의 서브 캡션.                                                                   |
| caption-font             | "\[weight] \[style] size family"                                                         |         |                     | 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"    |
| caption-font-family      | serif / sans-serif / monospace / 글꼴 이름                                                   | serif   |                     | 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                 |
| caption-font-size        | Float                                                                                    | 0.8     | em                  | 캡션의 글꼴 크기.                                                                    |
| caption-font-weight      | normal / bold                                                                            | normal  |                     | 캡션의 글꼴 가중치.                                                                   |
| caption-font-style       | normal / italic                                                                          | normal  |                     | 캡션의 글꼴 스타일.                                                                   |
| caption-font-no-scale    | Boolean                                                                                  | no      |                     | 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                              |
| subcaption-font          | "\[weight] \[style] size family"                                                         |         |                     | 서브 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace" |
| subcaption-font-family   | serif / sans-serif / monospace / 글꼴 이름                                                   | serif   |                     | 서브 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"              |
| subcaption-font-size     | Float                                                                                    | 0.6     | em                  | 서브 캡션의 글꼴 크기.                                                                 |
| subcaption-font-weight   | normal / bold                                                                            | normal  |                     | 서브 캡션의 글꼴 가중치.                                                                |
| subcaption-font-style    | normal / italic                                                                          | normal  |                     | 서브 캡션의 글꼴 스타일.                                                                |
| subcaption-font-no-scale | Boolean                                                                                  | no      |                     | 서브 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                           |
| caption-align            | left / right / center                                                                    | left    |                     | 캡션과 서브 캡션의 텍스트 정렬 방식.                                                         |
| caption-height           | Float                                                                                    | 0       | dp, em, layout의 상대값 | 캡션 영역의 높이.                                                                    |
| inner-caption            | Boolean                                                                                  | no      |                     | 캡션 영역을 이미지 영역 안으로 배치하려면 yes를 지정한다.                                            |
| caption-color            | Color                                                                                    | #000000 |                     | 캡션의 글자색.                                                                      |
| subcaption-color         | Color                                                                                    | #000000 |                     | 서브 캡션의 글자색.                                                                   |
| caption-background-color | Color                                                                                    | 투명      |                     | 캡션 영역의 배경색.                                                                   |

#### 액션 <a href="#_15" id="_15"></a>

N/A

#### 이벤트 <a href="#_16" id="_16"></a>

N/A

### 포토줌 (Photo Zoom) <a href="#photo-zoom" id="photo-zoom"></a>

* 지원 플랫폼: iOS
* 잼킷 버전: 1.0

#### 사용예 <a href="#_17" id="_17"></a>

```
=object photozoom: filename="photo.jpg"
```

#### 속성 <a href="#_18" id="_18"></a>

| 속성                       | 타입(허용값)                                                                                  | 기본값     | 단위                  | 설명                                                                            |
| ------------------------ | ---------------------------------------------------------------------------------------- | ------- | ------------------- | ----------------------------------------------------------------------------- |
| filename                 | 파일명                                                                                      | None    |                     | 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                           |
| image-url                | URL                                                                                      | None    |                     | 이미지의 URL. URL로 부터 이미지를 다운로드한다. 이 때, image-downloadable을 yes로 설정해야 한다.         |
| default-image            | 파일명                                                                                      | None    |                     | 이미지가 아직 로드되어 있지 않을 때 나타낼 기본 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.              |
| image-downloadable       | Boolean                                                                                  | no      |                     | 이미지를 외부에서 다운로드할 수 있을 때 yes로 지정한다. 기본 이미지는 다운로드 할 수 없다.                        |
| scale-mode               | fill / fit                                                                               | fill    |                     | 이미지가 오브젝트의 크기에 맞지 않을 경우에 사용될 확대/축소 모드.                                        |
| maximize-scale-mode      | fill / fit                                                                               | fit     |                     | 이미지가 전체화면으로 커졌을 경우에 사용될 확대/축소 모드.                                             |
| content-gravity          | left-top / left-bottom / right-top / right-bottom / top / right / bottom / left / center | center  |                     | 이미지가 확대/축소되어 표현되었을 때, 화면에 보여질 이미지의 위치를 지정한다.                                  |
| shadow-color             | Color                                                                                    | #000000 |                     | 이미지 그림자 효과에 사용될 색상.                                                           |
| dim-color                | Color                                                                                    | #ffffff |                     | 이미지가 전체화면으로 커졌을 경우 이미지 주변 배경에 사용될 색상.                                         |
| caption                  | String                                                                                   | None    |                     | 이미지의 캡션.                                                                      |
| subcaption               | String                                                                                   | None    |                     | 이미지의 서브 캡션.                                                                   |
| caption-font             | "\[weight] \[style] size family"                                                         |         |                     | 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"    |
| caption-font-family      | serif / sans-serif / monospace / 글꼴 이름                                                   | serif   |                     | 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                 |
| caption-font-size        | Float                                                                                    | 0.8     | em                  | 캡션의 글꼴 크기.                                                                    |
| caption-font-weight      | normal / bold                                                                            | normal  |                     | 캡션의 글꼴 가중치.                                                                   |
| caption-font-style       | normal / italic                                                                          | normal  |                     | 캡션의 글꼴 스타일.                                                                   |
| caption-font-no-scale    | Boolean                                                                                  | no      |                     | 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                              |
| subcaption-font          | "\[weight] \[style] size family"                                                         |         |                     | 서브 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace" |
| subcaption-font-family   | serif / sans-serif / monospace / 글꼴 이름                                                   | serif   |                     | 서브 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"              |
| subcaption-font-size     | Float                                                                                    | 0.6     | em                  | 서브 캡션의 글꼴 크기.                                                                 |
| subcaption-font-weight   | normal / bold                                                                            | normal  |                     | 서브 캡션의 글꼴 가중치.                                                                |
| subcaption-font-style    | normal / italic                                                                          | normal  |                     | 서브 캡션의 글꼴 스타일.                                                                |
| subcaption-font-no-scale | Boolean                                                                                  | no      |                     | 서브 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                           |
| caption-align            | left / right / center                                                                    | left    |                     | 캡션과 서브 캡션의 텍스트 정렬 방식.                                                         |
| caption-height           | Float                                                                                    | 0       | dp, em, layout의 상대값 | 캡션 영역의 높이.                                                                    |
| inner-caption            | Boolean                                                                                  | no      |                     | 캡션 영역을 이미지 영역 안으로 배치하려면 yes를 지정한다.                                            |
| caption-color            | Color                                                                                    | #000000 |                     | 캡션의 글자색.                                                                      |
| subcaption-color         | Color                                                                                    | #000000 |                     | 서브 캡션의 글자색.                                                                   |
| caption-background-color | Color                                                                                    | 투명      |                     | 캡션 영역의 배경색.                                                                   |

#### 액션 <a href="#_19" id="_19"></a>

N/A

#### 이벤트 <a href="#_20" id="_20"></a>

N/A

### 포토스크롤 (Photo Scroll) <a href="#photo-scroll" id="photo-scroll"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_21" id="_21"></a>

```
=object photoscroll: filename="photo.jpg"
```

#### 속성 <a href="#_22" id="_22"></a>

| 속성                       | 타입(허용값)                                | 기본값     | 단위                  | 설명                                                                            |
| ------------------------ | -------------------------------------- | ------- | ------------------- | ----------------------------------------------------------------------------- |
| filename                 | 파일명                                    | None    |                     | 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                           |
| image-url                | URL                                    | None    |                     | 이미지의 URL. URL로 부터 이미지를 다운로드한다. 이 때, image-downloadable을 yes로 설정해야 한다.         |
| default-image            | 파일명                                    | None    |                     | 이미지가 아직 로드되어 있지 않을 때 나타낼 기본 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.              |
| image-downloadable       | Boolean                                | no      |                     | 이미지를 외부에서 다운로드할 수 있을 때 yes로 지정한다. 기본 이미지는 다운로드 할 수 없다.                        |
| scale-mode               | fill / fit                             | fill    |                     | 이미지가 오브젝트의 크기에 맞지 않을 경우에 사용될 확대/축소 모드. fill 또는 fit을 지정할 수 있다.                 |
| max-scale                | Float                                  | 3       |                     | 이미지가 확대될 수 있는 최대 비율.                                                          |
| caption                  | String                                 | None    |                     | 이미지의 캡션.                                                                      |
| subcaption               | String                                 | None    |                     | 이미지의 서브 캡션.                                                                   |
| caption-font             | "\[weight] \[style] size family"       |         |                     | 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"    |
| caption-font-family      | serif / sans-serif / monospace / 글꼴 이름 | serif   |                     | 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                 |
| caption-font-size        | Float                                  | 0.8     | em                  | 캡션의 글꼴 크기.                                                                    |
| caption-font-weight      | normal / bold                          | normal  |                     | 캡션의 글꼴 가중치.                                                                   |
| caption-font-style       | normal / italic                        | normal  |                     | 캡션의 글꼴 스타일.                                                                   |
| caption-font-no-scale    | Boolean                                | no      |                     | 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                              |
| subcaption-font          | "\[weight] \[style] size family"       |         |                     | 서브 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace" |
| subcaption-font-family   | serif / sans-serif / monospace / 글꼴 이름 | serif   |                     | 서브 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"              |
| subcaption-font-size     | Float                                  | 0.6     | em                  | 서브 캡션의 글꼴 크기.                                                                 |
| subcaption-font-weight   | normal / bold                          | normal  |                     | 서브 캡션의 글꼴 가중치.                                                                |
| subcaption-font-style    | normal / italic                        | normal  |                     | 서브 캡션의 글꼴 스타일.                                                                |
| subcaption-font-no-scale | Boolean                                | no      |                     | 서브 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                           |
| caption-align            | left / right / center                  | left    |                     | 캡션과 서브 캡션의 텍스트 정렬 방식.                                                         |
| caption-height           | Float                                  | 0       | dp, em, layout의 상대값 | 캡션 영역의 높이.                                                                    |
| inner-caption            | Boolean                                | no      |                     | 캡션 영역을 이미지 영역 안으로 배치하려면 yes를 지정한다.                                            |
| caption-color            | Color                                  | #000000 |                     | 캡션의 글자색.                                                                      |
| subcaption-color         | Color                                  | #000000 |                     | 서브 캡션의 글자색.                                                                   |
| caption-background-color | Color                                  | 투명      |                     | 캡션 영역의 배경색.                                                                   |

#### 액션 <a href="#_23" id="_23"></a>

N/A

#### 이벤트 <a href="#_24" id="_24"></a>

N/A

### 멀티포토 (Multi Photo) <a href="#multi-photo" id="multi-photo"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_25" id="_25"></a>

```
=object multiphoto: photo-1="photo.jpg;캡션입니다.;서브캡션입니다.", photo-2="photo.jpg;캡션입니다.;서브캡션입니다.", photo-3="photo.jpg;캡션입니다.;서브캡션입니다."
```

#### 속성 <a href="#_26" id="_26"></a>

| 속성                       | 타입(허용값)                                | 기본값     | 단위 | 설명                                                                                |
| ------------------------ | -------------------------------------- | ------- | -- | --------------------------------------------------------------------------------- |
| photo-n                  | "파일명;캡션;서브캡션"                          |         |    | 이미지 파일명과 캡션을 하나로 묶어 이미지를 지정함. 이미지가 여러 장일 때에는 photo-1="...", photo-2="..." 등으로 지정. |
| scale-mode               | fill / fit                             | fill    |    | 이미지가 오브젝트의 크기에 맞지 않을 경우에 사용될 확대/축소 모드.                                            |
| dim-color                | Color                                  | #ffffff |    | 이미지가 전체화면으로 커졌을 경우 이미지 주변 배경에 사용될 색상.                                             |
| caption                  | String                                 | None    |    | 이미지의 캡션.                                                                          |
| subcaption               | String                                 | None    |    | 이미지의 서브 캡션.                                                                       |
| caption-font             | "\[weight] \[style] size family"       |         |    | 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"        |
| caption-font-family      | serif / sans-serif / monospace / 글꼴 이름 | serif   |    | 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                     |
| caption-font-size        | Float                                  | 0.8     | em | 캡션의 글꼴 크기.                                                                        |
| caption-font-weight      | normal / bold                          | normal  |    | 캡션의 글꼴 가중치.                                                                       |
| caption-font-style       | normal / italic                        | normal  |    | 캡션의 글꼴 스타일.                                                                       |
| caption-font-no-scale    | Boolean                                | no      |    | 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                                  |
| subcaption-font          | "\[weight] \[style] size family"       |         |    | 서브 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"     |
| subcaption-font-family   | serif / sans-serif / monospace / 글꼴 이름 | serif   |    | 서브 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                  |
| subcaption-font-size     | Float                                  | 0.6     | em | 서브 캡션의 글꼴 크기.                                                                     |
| subcaption-font-weight   | normal / bold                          | normal  |    | 서브 캡션의 글꼴 가중치.                                                                    |
| subcaption-font-style    | normal / italic                        | normal  |    | 서브 캡션의 글꼴 스타일.                                                                    |
| subcaption-font-no-scale | Boolean                                | no      |    | 서브 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                               |
| caption-align            | left / right / center                  | left    |    | 캡션과 서브 캡션의 텍스트 정렬 방식.                                                             |
| caption-height           | Float                                  | 0       |    | 캡션 영역의 높이.                                                                        |
| inner-caption            | Boolean                                | no      |    | 캡션 영역을 이미지 영역 안으로 배치하려면 yes를 지정한다.                                                |
| caption-color            | Color                                  | #000000 |    | 캡션의 글자색.                                                                          |
| subcaption-color         | Color                                  | #000000 |    | 서브 캡션의 글자색.                                                                       |
| caption-background-color | Color                                  | 투명      |    | 캡션 영역의 배경색.                                                                       |

#### 액션 <a href="#_27" id="_27"></a>

N/A

#### 이벤트 <a href="#_28" id="_28"></a>

N/A

### 포토롤 (Photo Roll) <a href="#photo-roll" id="photo-roll"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_29" id="_29"></a>

```
=object photoroll: photo-1="photo.jpg;메인캡션;서브캡션", photo-2="photo.jpg;메인캡션;서브캡션", photo-3="photo.jpg;메인캡션;서브캡션"
```

#### 속성 <a href="#_30" id="_30"></a>

| 속성                       | 타입(허용값)                                | 기본값     | 단위                  | 설명                                                                                |
| ------------------------ | -------------------------------------- | ------- | ------------------- | --------------------------------------------------------------------------------- |
| photo-n                  | "파일명;캡션;서브캡션"                          |         |                     | 이미지 파일명과 캡션을 하나로 묶어 이미지를 지정함. 이미지가 여러 장일 때에는 photo-1="...", photo-2="..." 등으로 지정. |
| photo-width              | Float                                  | 0       | dp, em, layout의 상대값 | 이미지 썸네일 한장의 너비. 0으로 지정한 경우, 자동으로 계산한다.                                            |
| photo-spacing            | Float                                  | 0       | dp, em, layout의 상대값 | 이미지 썸네일 사이의 간격.                                                                   |
| maximize-scale-mode      | fill / fit                             | fill    |                     | 이미지가 전체화면으로 커졌을 경우에 사용될 확대/축소 모드.                                                 |
| dim-color                | Color                                  | #ffffff |                     | 이미지가 전체화면으로 커졌을 경우 이미지 주변 배경에 사용될 색상.                                             |
| caption                  | String                                 | None    |                     | 이미지의 캡션.                                                                          |
| subcaption               | String                                 | None    |                     | 이미지의 서브 캡션.                                                                       |
| caption-font             | "\[weight] \[style] size family"       |         |                     | 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"        |
| caption-font-family      | serif / sans-serif / monospace / 글꼴 이름 | serif   |                     | 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                     |
| caption-font-size        | Float                                  | 0.8     | em                  | 캡션의 글꼴 크기.                                                                        |
| caption-font-weight      | normal / bold                          | normal  |                     | 캡션의 글꼴 가중치.                                                                       |
| caption-font-style       | normal / italic                        | normal  |                     | 캡션의 글꼴 스타일.                                                                       |
| caption-font-no-scale    | Boolean                                | no      |                     | 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                                  |
| subcaption-font          | "\[weight] \[style] size family"       |         |                     | 서브 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"     |
| subcaption-font-family   | serif / sans-serif / monospace / 글꼴 이름 | serif   |                     | 서브 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                  |
| subcaption-font-size     | Float                                  | 0.6     | em                  | 서브 캡션의 글꼴 크기.                                                                     |
| subcaption-font-weight   | normal / bold                          | normal  |                     | 서브 캡션의 글꼴 가중치.                                                                    |
| subcaption-font-style    | normal / italic                        | normal  |                     | 서브 캡션의 글꼴 스타일.                                                                    |
| subcaption-font-no-scale | Boolean                                | no      |                     | 서브 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                               |
| caption-align            | left / right / center                  | left    |                     | 캡션과 서브 캡션의 텍스트 정렬 방식.                                                             |
| caption-height           | Float                                  | 0       | dp, em, layout의 상대값 | 캡션 영역의 높이.                                                                        |
| inner-caption            | Boolean                                | no      |                     | 캡션 영역을 이미지 영역 안으로 배치하려면 yes를 지정한다.                                                |
| caption-color            | Color                                  | #000000 |                     | 캡션의 글자색.                                                                          |
| subcaption-color         | Color                                  | #000000 |                     | 서브 캡션의 글자색.                                                                       |
| caption-background-color | Color                                  | 투명      |                     | 캡션 영역의 배경색.                                                                       |

#### 액션 <a href="#_31" id="_31"></a>

N/A

#### 이벤트 <a href="#_32" id="_32"></a>

N/A

### 코믹 (Comic) <a href="#comic" id="comic"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_33" id="_33"></a>

```
=object comic: image="comic.jpg"
```

#### 속성 <a href="#_34" id="_34"></a>

| 속성                 | 타입(허용값)             | 기본값  | 단위 | 설명                                                                    |
| ------------------ | ------------------- | ---- | -- | --------------------------------------------------------------------- |
| image              | 파일명                 | None |    | 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                   |
| image-url          | URL                 | None |    | 이미지의 URL. URL로 부터 이미지를 다운로드한다. 이 때, image-downloadable을 yes로 설정해야 한다. |
| default-image      | 파일명                 | None |    | 이미지가 아직 로드되어 있지 않을 때 나타낼 기본 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.      |
| image-downloadable | Boolean             | no   |    | 이미지를 외부에서 다운로드할 수 있을 때 yes로 지정한다. 기본 이미지는 다운로드 할 수 없다.                |
| scale-mode         | fill / fit          | fill |    | 이미지가 오브젝트의 크기에 맞지 않을 경우에 사용될 확대/축소 모드.                                |
| zoomable           | Boolean             | yes  |    | 핀치 액션으로 이미지의 확대/축소가 가능하게 하려면 yes를 지정한다.                               |
| gutter-align       | left / right / none | none |    | 거터 이미지의 위치를 지정한다.                                                     |
| gutter-hidden      | Boolean             | yes  |    | 거터 이미지를 보이게 하려면 no를 지정한다.                                             |

#### 액션 <a href="#_35" id="_35"></a>

N/A

#### 이벤트 <a href="#_36" id="_36"></a>

N/A

### 지도 (Map) <a href="#map" id="map"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_37" id="_37"></a>

```
=object map: latitude="37.566535", longitude="126.977969", zoom-level="17"
```

#### 속성 <a href="#_38" id="_38"></a>

| 속성                       | 타입(허용값)                                | 기본값        | 단위                  | 설명                                                                            |
| ------------------------ | -------------------------------------- | ---------- | ------------------- | ----------------------------------------------------------------------------- |
| latitude                 | Float                                  | 37.566535  |                     | 지도의 위도.                                                                       |
| longitude                | Float                                  | 126.977969 |                     | 지도의 경도.                                                                       |
| zoom-level               | Float                                  | 17         |                     | 지도의 확대/축소 레벨.                                                                 |
| title                    | String                                 | None       |                     | 장소 마크에 표시될 제목.                                                                |
| subtitle                 | String                                 | None       |                     | 장소 마크에 표시될 부제목.                                                               |
| caption                  | String                                 | None       |                     | 이미지의 캡션.                                                                      |
| subcaption               | String                                 | None       |                     | 이미지의 서브 캡션.                                                                   |
| caption-font             | "\[weight] \[style] size family"       |            |                     | 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"    |
| caption-font-family      | serif / sans-serif / monospace / 글꼴 이름 | serif      |                     | 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                 |
| caption-font-size        | Float                                  | 0.8        | em                  | 캡션의 글꼴 크기.                                                                    |
| caption-font-weight      | normal / bold                          | normal     |                     | 캡션의 글꼴 가중치.                                                                   |
| caption-font-style       | normal / italic                        | normal     |                     | 캡션의 글꼴 스타일.                                                                   |
| caption-font-no-scale    | Boolean                                | no         |                     | 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                              |
| subcaption-font          | "\[weight] \[style] size family"       |            |                     | 서브 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace" |
| subcaption-font-family   | serif / sans-serif / monospace / 글꼴 이름 | serif      |                     | 서브 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"              |
| subcaption-font-size     | Float                                  | 0.6        | em                  | 서브 캡션의 글꼴 크기.                                                                 |
| subcaption-font-weight   | normal / bold                          | normal     |                     | 서브 캡션의 글꼴 가중치.                                                                |
| subcaption-font-style    | normal / italic                        | normal     |                     | 서브 캡션의 글꼴 스타일.                                                                |
| subcaption-font-no-scale | Boolean                                | no         |                     | 서브 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                           |
| caption-align            | left / right / center                  | left       |                     | 캡션과 서브 캡션의 텍스트 정렬 방식.                                                         |
| caption-height           | Float                                  | 0          | dp, em, layout의 상대값 | 캡션 영역의 높이.                                                                    |
| inner-caption            | Boolean                                | no         |                     | 캡션 영역을 이미지 영역 안으로 배치하려면 yes를 지정한다.                                            |
| caption-color            | Color                                  | #000000    |                     | 캡션의 글자색.                                                                      |
| subcaption-color         | Color                                  | #000000    |                     | 서브 캡션의 글자색.                                                                   |
| caption-background-color | Color                                  | 투명         |                     | 캡션 영역의 배경색.                                                                   |

#### 액션 <a href="#_39" id="_39"></a>

N/A

#### 이벤트 <a href="#_40" id="_40"></a>

N/A

### 미니지도 (Mini Map) <a href="#mini-map" id="mini-map"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_41" id="_41"></a>

```
=object minimap: latitude="37.566535", longitude="126.977969", zoom-level="17"
```

#### 속성 <a href="#_42" id="_42"></a>

| 속성         | 타입(허용값) | 기본값        | 단위 | 설명              |
| ---------- | ------- | ---------- | -- | --------------- |
| latitude   | Float   | 37.566535  |    | 지도의 위도.         |
| longitude  | Float   | 126.977969 |    | 지도의 경도.         |
| zoom-level | Float   | 17         |    | 지도의 확대/축소 레벨.   |
| title      | String  | None       |    | 장소 마크에 표시될 제목.  |
| subtitle   | String  | None       |    | 장소 마크에 표시될 부제목. |

#### 액션 <a href="#_43" id="_43"></a>

N/A

#### 이벤트 <a href="#_44" id="_44"></a>

N/A

### 라벨 (Label) <a href="#label" id="label"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_45" id="_45"></a>

```
=object label: text="라벨"
```

#### 속성 <a href="#_46" id="_46"></a>

| 속성              | 타입(허용값)                                                                            | 기본값            | 단위                  | 설명                                                                                  |
| --------------- | ---------------------------------------------------------------------------------- | -------------- | ------------------- | ----------------------------------------------------------------------------------- |
| text            | String                                                                             | None           |                     | 라벨 텍스트.                                                                             |
| waiting-text    | String                                                                             | None           |                     | 라벨 텍스트가 지정될 때까지 표시될 대기용 텍스트.                                                        |
| font            | "\[weight] \[style] size family"                                                   |                |                     | 라벨 텍스트의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"      |
| font-family     | serif / sans-serif / monospace / 글꼴 이름                                             | serif          |                     | 라벨 텍스트의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                   |
| font-size       | Float                                                                              | 0.8            | em                  | 라벨 텍스트의 글꼴 크기.                                                                      |
| font-weight     | normal / bold                                                                      | normal         |                     | 라벨 텍스트의 글꼴 가중치.                                                                     |
| font-style      | normal / italic                                                                    | normal         |                     | 라벨 텍스트의 글꼴 스타일.                                                                     |
| font-no-scale   | Boolean                                                                            | no             |                     | 라벨 텍스트의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                                |
| text-align      | left / right / center                                                              | left           |                     | 라벨 텍스트의 정렬 방식.                                                                      |
| line-break-mode | word-wrap / character-wrap / tail-truncation / middle-truncation / head-truncation | character-wrap |                     | 라벨 텍스트가 여러 줄로 나뉘었을 때 줄을 나누는 방법.                                                     |
| number-of-lines | Integer                                                                            | 1              |                     | 라벨 텍스트가 여러 줄로 나뉘게 되었을 경우 최대 허용할 줄의 수. 0을 지정하면 무제한 허용.                               |
| text-color      | Color                                                                              | #000000        |                     | 라벨 텍스트의 색상.                                                                         |
| shadow-color    | Color                                                                              | #cccccc        |                     | 라벨 텍스트 그림자 효과의 색상.                                                                  |
| shadow-offset   | Float                                                                              | 0              |                     | 라벨 텍스트 그림자 효과의 위치. 양수를 지정하면 텍스트의 우하단 방향으로 그림자가 생기며, 음수를 지정하면 텍스트의 좌상단 방향으로 그림자가 생김. |
| content-padding | Side                                                                               | "0 0 0 0"      | dp, em, layout의 상대값 | 라벨 텍스트 영역의 패딩값. 축약형 사용 가능. 예) "1em", "1em 20dp", "1em 1.5em 0 1.2em"                |

#### 액션 <a href="#_47" id="_47"></a>

N/A

#### 이벤트 <a href="#_48" id="_48"></a>

N/A

### 버튼 (Button) <a href="#button" id="button"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_49" id="_49"></a>

```
=object button: label="클릭"
=object button: image="click.jpg", highlight-image="clicked.jpg"
```

#### 속성 <a href="#_50" id="_50"></a>

| 속성                         | 타입(허용값)                                                                            | 기본값            | 단위                  | 설명                                                                                                |
| -------------------------- | ---------------------------------------------------------------------------------- | -------------- | ------------------- | ------------------------------------------------------------------------------------------------- |
| label                      | String                                                                             | None           |                     | 보통 상태일 때의 라벨 텍스트.                                                                                 |
| selected-label             | String                                                                             | None           |                     | 선택된 상태일 때의 라벨 텍스트.                                                                                |
| disable-label              | String                                                                             | None           |                     | 비활성 상태일 때의 라벨 텍스트.                                                                                |
| image                      | 파일명                                                                                | None           |                     | 보통 상태일 때의 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                                     |
| image-url                  | URL                                                                                | None           |                     | 보통 상태일 때의 이미지의 URL. URL로 부터 이미지를 다운로드한다. 이 때, image-downloadable을 yes로 설정해야 한다.                   |
| highlight-image            | 파일명                                                                                | None           |                     | 하이라이트 상태일 때의 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                                  |
| selected-image             | 파일명                                                                                | None           |                     | 선택된 상태일 때의 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                                    |
| disable-image              | 파일명                                                                                | None           |                     | 비활성 상태일 때의 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                                    |
| mask-image                 | 파일명                                                                                | None           |                     | 모든 상태의 이미지 위에 겹쳐지는 마스크 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다. 마스크 이미지는 정가운데 한점을 중심으로 9-patch로 표현된다. |
| default-image              | 파일명                                                                                | None           |                     | 이미지가 아직 로드되어 있지 않을 때 나타낼 기본 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                  |
| image-downloadable         | Boolean                                                                            | no             |                     | 이미지를 외부에서 다운로드할 수 있을 때 yes로 지정한다. 마스크 이미지와 기본 이미지는 다운로드 할 수 없다.                                   |
| label-font                 | "\[weight] \[style] size family"                                                   |                |                     | 라벨 텍스트의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"                    |
| label-font-family          | serif / sans-serif / monospace / 글꼴 이름                                             | serif          |                     | 라벨 텍스트의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                                 |
| label-font-size            | Float                                                                              | 0.8            | em                  | 라벨 텍스트의 글꼴 크기.                                                                                    |
| label-font-weight          | normal / bold                                                                      | normal         |                     | 라벨 텍스트의 글꼴 가중치.                                                                                   |
| label-font-style           | normal / italic                                                                    | normal         |                     | 라벨 텍스트의 글꼴 스타일.                                                                                   |
| label-font-no-scale        | Boolean                                                                            | no             |                     | 라벨 텍스트의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                                              |
| label-align                | left / right / center                                                              | left           |                     | 라벨 텍스트의 정렬 방식.                                                                                    |
| line-break-mode            | word-wrap / character-wrap / tail-truncation / middle-truncation / head-truncation | character-wrap |                     | 라벨 텍스트가 여러 줄로 나뉘었을 때 줄을 나누는 방법.                                                                   |
| number-of-lines            | Integer                                                                            | 1              |                     | 라벨 텍스트가 여러 줄로 나뉘게 되었을 경우 최대 허용할 줄의 수. 0을 지정하면 무제한 허용.                                             |
| label-hidden               | Boolean                                                                            | no             |                     | 라벨 텍스트를 숨기려면 yes를 지정한다.                                                                           |
| label-color                | Color                                                                              | 투명             |                     | 보통 상태일 때의 라벨 텍스트 색상.                                                                              |
| highlight-label-color      | Color                                                                              | 투명             |                     | 하이라이트 상태일 때의 라벨 텍스트 색상.                                                                           |
| selected-label-color       | Color                                                                              | 투명             |                     | 선택된 상태일 때의 라벨 텍스트 색상.                                                                             |
| disable-label-color        | Color                                                                              | 투명             |                     | 비활성 상태일 때의 라벨 텍스트 색상.                                                                             |
| highlight-background-color | Color                                                                              | 투명             |                     | 하이라이트 상태일 때의 배경색.                                                                                 |
| selected-background-color  | Color                                                                              | 투명             |                     | 선택된 상태일 때의 배경색.                                                                                   |
| disable-background-color   | Color                                                                              | 투명             |                     | 비활성 상태일 때의 배경색.                                                                                   |
| content-padding            | Side                                                                               | "0 0 0 0"      | dp, em, layout의 상대값 | 라벨 텍스트 영역의 패딩값. 축약형 사용 가능. 예) "1em", "1em 20dp", "1em 1.5em 0 1.2em"                              |
| scale-mode                 | fill / fit                                                                         | fill           |                     | 버튼 이미지가 오브젝트의 크기에 맞지 않을 경우에 사용될 확대/축소 모드.                                                         |
| enabled                    | Boolean                                                                            | yes            |                     | 버튼을 비활성 상태로 만들려면 yes를 지정한다.                                                                       |
| selected                   | Boolean                                                                            | no             |                     | 버튼을 선택된 상태로 만들려면 yes를 지정한다.                                                                       |
| hides-when-disabled        | Boolean                                                                            | no             |                     | 버튼이 비활성화될 때 숨기려면 yes를 지정한다.                                                                       |
| disable-when-selected      | Boolean                                                                            | no             |                     | 버튼이 선택될 때 비활성화 하려면 yes를 지정한다.                                                                     |
| hides-when-selected        | Boolean                                                                            | no             |                     | 버튼이 선택될 때 숨기려면 yes를 지정한다.                                                                         |

#### 액션 <a href="#_51" id="_51"></a>

N/A

#### 이벤트 <a href="#_52" id="_52"></a>

| 이벤트 액션명 | 설명             |
| ------- | -------------- |
| action  | 버튼을 눌렀을 때 발생함. |

### 텍스트필드 (Textfield) <a href="#textfield" id="textfield"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_53" id="_53"></a>

```
=object textfield: placeholder="여기에 입력하세요."
```

#### 속성 <a href="#_54" id="_54"></a>

| 속성                       | 타입(허용값)                                                                            | 기본값     | 단위 | 설명                                                                             |
| ------------------------ | ---------------------------------------------------------------------------------- | ------- | -- | ------------------------------------------------------------------------------ |
| text                     | String                                                                             | None    |    | 텍스트 필드에 채워질 입력 텍스트                                                             |
| placeholder              | String                                                                             | None    |    | 텍스트 입력 힌트. 입력이 시작되면 사라진다.                                                      |
| font                     | "\[weight] \[style] size family"                                                   |         |    | 입력 텍스트의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace" |
| font-family              | serif / sans-serif / monospace / 글꼴 이름                                             | serif   |    | 입력 텍스트의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"              |
| font-size                | Float                                                                              | 0.8     | em | 입력 텍스트의 글꼴 크기.                                                                 |
| font-weight              | normal / bold                                                                      | normal  |    | 입력 텍스트의 글꼴 가중치.                                                                |
| font-style               | normal / italic                                                                    | normal  |    | 입력 텍스트의 글꼴 스타일.                                                                |
| font-no-scale            | Boolean                                                                            | no      |    | 입력 텍스트의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                           |
| text-align               | left / right / center                                                              | left    |    | 입력 텍스트의 정렬 방식.                                                                 |
| text-color               | Color                                                                              | #000000 |    | 입력 텍스트의 색상.                                                                    |
| disable-text-color       | Color                                                                              | #000000 |    | 비활성 상태의 입력 텍스트 색상.                                                             |
| placeholder-color        | Color                                                                              | #646464 |    | 텍스트 입력 힌트의 색상. (현재 iOS는 지원하지 않는다.)                                             |
| editable                 | Boolean                                                                            | yes     |    | 입력이 불가능한 상태로 만들려면 no를 지정한다.                                                    |
| secure                   | Boolean                                                                            | no      |    | 입력 보안을 설정하려면 yes를 지정한다. 비밀번호 입력 등에서 사용할 수 있다.                                  |
| keyboard-type            | default / email / url / number / decimal / phone / name-phone / twitter / alphabet | default |    | 텍스트 입력 시에 사용할 키보드 종류.                                                          |
| return-key-type          | default / next / done / join / go / search / send                                  | default |    | 키보드의 리턴키를 상황에 맞는 단어로 변경하기 위해서 지정한다.                                            |
| auto-capitalization-type | word / all / none                                                                  | word    |    | 텍스트 입력 시에 적용될 자동 대문자 타입.                                                       |
|                          |                                                                                    |         |    |                                                                                |

#### 액션 <a href="#_55" id="_55"></a>

N/A

#### 이벤트 <a href="#_56" id="_56"></a>

| 이벤트 액션명 | 설명                         |
| ------- | -------------------------- |
| action  | 텍스트를 입력한 후 리턴키를 눌렀을 때 발생함. |

### 텍스트 입력창 (Text) <a href="#text" id="text"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_57" id="_57"></a>

```
=object text: text="여기에 입력하세요."
```

#### 속성 <a href="#_58" id="_58"></a>

| 속성            | 타입(허용값)                                | 기본값     | 단위 | 설명                                                                             |
| ------------- | -------------------------------------- | ------- | -- | ------------------------------------------------------------------------------ |
| text          | String                                 | None    |    | 텍스트 입력창에 채워질 입력 텍스트                                                            |
| font          | "\[weight] \[style] size family"       |         |    | 입력 텍스트의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace" |
| font-family   | serif / sans-serif / monospace / 글꼴 이름 | serif   |    | 입력 텍스트의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"              |
| font-size     | Float                                  | 0.8     | em | 입력 텍스트의 글꼴 크기.                                                                 |
| font-weight   | normal / bold                          | normal  |    | 입력 텍스트의 글꼴 가중치.                                                                |
| font-style    | normal / italic                        | normal  |    | 입력 텍스트의 글꼴 스타일.                                                                |
| font-no-scale | Boolean                                | no      |    | 입력 텍스트의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                           |
| text-color    | Color                                  | #000000 |    | 입력 텍스트의 색상.                                                                    |
| editable      | Boolean                                | yes     |    | 입력이 불가능한 상태로 만들려면 no를 지정한다.                                                    |

#### 액션 <a href="#_59" id="_59"></a>

N/A

#### 이벤트 <a href="#_60" id="_60"></a>

N/A

### 체크박스 (CheckBox) <a href="#checkbox" id="checkbox"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_61" id="_61"></a>

```
=object checkbox: image="normal.jpg", selected-image="selected.jpg"
```

#### 속성 <a href="#_62" id="_62"></a>

| 속성                         | 타입(허용값)                                                                            | 기본값            | 단위                  | 설명                                                                              |
| -------------------------- | ---------------------------------------------------------------------------------- | -------------- | ------------------- | ------------------------------------------------------------------------------- |
| label                      | String                                                                             | None           |                     | 보통 상태일 때의 라벨 텍스트.                                                               |
| selected-label             | String                                                                             | None           |                     | 선택된 상태일 때의 라벨 텍스트.                                                              |
| disable-label              | String                                                                             | None           |                     | 비활성 상태일 때의 라벨 텍스트.                                                              |
| image                      | 파일명                                                                                | None           |                     | 보통 상태일 때의 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                   |
| image-url                  | URL                                                                                | None           |                     | 보통 상태일 때의 이미지의 URL. URL로 부터 이미지를 다운로드한다. 이 때, image-downloadable을 yes로 설정해야 한다. |
| highlight-image            | 파일명                                                                                | None           |                     | 하이라이트 상태일 때의 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                |
| selected-image             | 파일명                                                                                | None           |                     | 선택된 상태일 때의 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                  |
| disable-image              | 파일명                                                                                | None           |                     | 비활성 상태일 때의 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                  |
| answer-image               | 파일명                                                                                | None           |                     | 체크박스의 정답을 나타낼 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                              |
| default-image              | 파일명                                                                                | None           |                     | 이미지가 아직 로드되어 있지 않을 때 나타낼 기본 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                |
| content-background-image   | 파일명                                                                                | None           |                     | 보통 상태일 때의 배경 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                                |
| highlight-background-image | 파일명                                                                                | None           |                     | 하이라이트 상태일 때의 배경 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                             |
| selected-background-image  | 파일명                                                                                | None           |                     | 선택된 상태일 때의 배경 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                               |
| disable-background-image   | 파일명                                                                                | None           |                     | 비활성 상태일 때의 배경 이미지 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                               |
| image-downloadable         | Boolean                                                                            | no             |                     | 이미지를 외부에서 다운로드할 수 있을 때 yes로 지정한다. 마스크 이미지와 기본 이미지는 다운로드 할 수 없다.                 |
| label-font                 | "\[weight] \[style] size family"                                                   |                |                     | 라벨 텍스트의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"  |
| label-font-family          | serif / sans-serif / monospace / 글꼴 이름                                             | serif          |                     | 라벨 텍스트의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"               |
| label-font-size            | Float                                                                              | 0.8            | em                  | 라벨 텍스트의 글꼴 크기.                                                                  |
| label-font-weight          | normal / bold                                                                      | normal         |                     | 라벨 텍스트의 글꼴 가중치.                                                                 |
| label-font-style           | normal / italic                                                                    | normal         |                     | 라벨 텍스트의 글꼴 스타일.                                                                 |
| label-font-no-scale        | Boolean                                                                            | no             |                     | 라벨 텍스트의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                            |
| label-align                | left / right / center                                                              | left           |                     | 라벨 텍스트의 정렬 방식.                                                                  |
| line-break-mode            | word-wrap / character-wrap / tail-truncation / middle-truncation / head-truncation | character-wrap |                     | 라벨 텍스트가 여러 줄로 나뉘었을 때 줄을 나누는 방법.                                                 |
| number-of-lines            | Integer                                                                            | 1              |                     | 라벨 텍스트가 여러 줄로 나뉘게 되었을 경우 최대 허용할 줄의 수. 0을 지정하면 무제한 허용.                           |
| label-hidden               | Boolean                                                                            | no             |                     | 라벨 텍스트를 숨기려면 yes를 지정한다.                                                         |
| label-color                | Color                                                                              | 투명             |                     | 보통 상태일 때의 라벨 텍스트 색상.                                                            |
| highlight-label-color      | Color                                                                              | 투명             |                     | 하이라이트 상태일 때의 라벨 텍스트 색상.                                                         |
| selected-label-color       | Color                                                                              | 투명             |                     | 선택된 상태일 때의 라벨 텍스트 색상.                                                           |
| disable-label-color        | Color                                                                              | 투명             |                     | 비활성 상태일 때의 라벨 텍스트 색상.                                                           |
| highlight-background-color | Color                                                                              | 투명             |                     | 하이라이트 상태일 때의 배경색.                                                               |
| selected-background-color  | Color                                                                              | 투명             |                     | 선택된 상태일 때의 배경색.                                                                 |
| disable-background-color   | Color                                                                              | 투명             |                     | 비활성 상태일 때의 배경색.                                                                 |
| content-padding            | Side                                                                               | "0 0 0 0"      | dp, em, layout의 상대값 | 라벨 텍스트 영역의 패딩값. 축약형 사용 가능. 예) "1em", "1em 20dp", "1em 1.5em 0 1.2em"            |
| content-spacing            | Float                                                                              | 0              | dp, em, layout의 상대값 | 이미지와 라벨 텍스트 사이의 간격.                                                             |
| select-mode                | single / multiple / none                                                           | none           |                     | 그룹 체크박스의 선택 모드.                                                                 |
| scale-mode                 | fill / fit                                                                         | fill           |                     | 체크박스 이미지가 오브젝트의 크기에 맞지 않을 경우에 사용될 확대/축소 모드.                                     |
| enabled                    | Boolean                                                                            | yes            |                     | 체크박스를 비활성화 상태로 만들려면 yes를 지정한다.                                                  |
| selected                   | Boolean                                                                            | no             |                     | 체크박스를 선택된 상태로 만들려면 yes를 지정한다.                                                   |
| hides-when-disabled        | Boolean                                                                            | no             |                     | 체크박스가 비활성화될 때 숨기려면 yes를 지정한다.                                                   |
| disable-when-selected      | Boolean                                                                            | no             |                     | 체크박스가 선택될 때 비활성화 하려면 yes를 지정한다.                                                 |
| hides-when-selected        | Boolean                                                                            | no             |                     | 체크박스가 선택될 때 숨기려면 yes를 지정한다.                                                     |

#### 액션 <a href="#_63" id="_63"></a>

N/A

#### 이벤트 <a href="#_64" id="_64"></a>

| 이벤트 액션명                | 설명                                            |
| ---------------------- | --------------------------------------------- |
| action                 | 버튼을 눌렀을 때 발생함.                                |
| action-when-selected   | 버튼을 눌러 선택된 상태가 되었을 때 발생함. action과 중복으로 발생.    |
| action-when-deselected | 버튼을 눌러 선택된 상태가 해제 되었을 때 발생함. action과 중복으로 발생. |

### 초이스 (Choices) <a href="#choices" id="choices"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_65" id="_65"></a>

```
=object choices: choice-1="(1);보기 1", choice-2="(2);보기 2", choice-3="(3);보기 3", choice-image="selected.jpg"
```

#### 속성 <a href="#_66" id="_66"></a>

| 속성                | 타입(허용값)                                                                            | 기본값            | 단위 | 설명                                                                                  |
| ----------------- | ---------------------------------------------------------------------------------- | -------------- | -- | ----------------------------------------------------------------------------------- |
| choice-n          | "심볼;보기"                                                                            |                |    | 심볼과 보기 텍스트를 하나로 묶어 선택항을 지정함. 선택항이 여러 개일 때에는 choice-1="...", choice-2="..." 등으로 지정.  |
| blank-text        | String                                                                             | None           |    | 문제의 빈칸을 표현할 텍스트.                                                                    |
| number            | String                                                                             | None           |    | 문항 번호.                                                                              |
| answer            | String                                                                             | None           |    | 정답 번호.                                                                              |
| check-image       | 파일명                                                                                | None           |    | 보기를 선택할 때 심볼 위에 나타날 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                            |
| answer-image      | 파일명                                                                                | None           |    | 정답 확인 시 심볼 위에 나타날 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                              |
| font              | "\[weight] \[style] size family"                                                   |                |    | 심볼 및 보기 텍스트의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace" |
| font-family       | serif / sans-serif / monospace / 글꼴 이름                                             | serif          |    | 심볼 및 보기 텍스트의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"              |
| font-size         | Float                                                                              | 0.8            | em | 심볼 및 보기 텍스트의 글꼴 크기.                                                                 |
| font-weight       | normal / bold                                                                      | normal         |    | 심볼 및 보기 텍스트의 글꼴 가중치.                                                                |
| font-style        | normal / italic                                                                    | normal         |    | 심볼 및 보기 텍스트의 글꼴 스타일.                                                                |
| font-no-scale     | Boolean                                                                            | no             |    | 심볼 및 보기 텍스트의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                           |
| line-break-mode   | word-wrap / character-wrap / tail-truncation / middle-truncation / head-truncation | character-wrap |    | 보기 텍스트가 여러 줄로 나뉘었을 때 줄을 나누는 방법.                                                     |
| paragraph-spacing | Float                                                                              | 0              |    | 보기 항목 간의 문단 간격.                                                                     |

#### 액션 <a href="#_67" id="_67"></a>

N/A

#### 이벤트 <a href="#_68" id="_68"></a>

N/A

### 입력 (Input) <a href="#input" id="input"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_69" id="_69"></a>

```
=object input: id="key", value="value"
```

#### 속성 <a href="#_70" id="_70"></a>

| 속성    | 타입(허용값) | 기본값  | 단위 | 설명 |
| ----- | ------- | ---- | -- | -- |
| id    | String  | None |    |    |
| value | String  | None |    |    |

#### 액션 <a href="#_71" id="_71"></a>

N/A

#### 이벤트 <a href="#_72" id="_72"></a>

N/A

### 비디오 (Video) <a href="#video" id="video"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_73" id="_73"></a>

```
=object video: filename="sample.mp4"
=object video: url="http://www.video.org / sample.mp4"
```

#### 속성 <a href="#_74" id="_74"></a>

| 속성                       | 타입(허용값)                                | 기본값     | 단위                  | 설명                                                                            |
| ------------------------ | -------------------------------------- | ------- | ------------------- | ----------------------------------------------------------------------------- |
| filename                 | 파일명                                    | None    |                     | 비디오 파일명. 파일은 Videos 디렉토리에 들어있어야 한다.                                           |
| url                      | URL                                    | None    |                     | 비디오의 URL.                                                                     |
| autoplay                 | Boolean                                | no      |                     | 오브젝트가 활성화될 때 자동으로 비디오를 재생하려면 yes를 지정한다.                                       |
| loop                     | Boolean                                | no      |                     | 비디오를 반복하여 재생하려면 yes를 지정한다.                                                    |
| control-hidden           | Boolean                                | no      |                     | 비디오 제어 창을 숨기려면 yes를 지정한다.                                                     |
| preview-image            | 파일명                                    | None    |                     | 비디오가 재생되기 전에 나타날 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                         |
| image-downloadable       | Boolean                                | no      |                     | 이미지를 외부에서 다운로드할 수 있을 때 yes로 지정한다.                                             |
| caption                  | String                                 | None    |                     | 비디오의 캡션.                                                                      |
| subcaption               | String                                 | None    |                     | 비디오의 서브 캡션.                                                                   |
| caption-font             | "\[weight] \[style] size family"       |         |                     | 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"    |
| caption-font-family      | serif / sans-serif / monospace / 글꼴 이름 | serif   |                     | 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                 |
| caption-font-size        | Float                                  | 0.8     | em                  | 캡션의 글꼴 크기.                                                                    |
| caption-font-weight      | normal / bold                          | normal  |                     | 캡션의 글꼴 가중치.                                                                   |
| caption-font-style       | normal / italic                        | normal  |                     | 캡션의 글꼴 스타일.                                                                   |
| caption-font-no-scale    | Boolean                                | no      |                     | 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                              |
| subcaption-font          | "\[weight] \[style] size family"       |         |                     | 서브 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace" |
| subcaption-font-family   | serif / sans-serif / monospace / 글꼴 이름 | serif   |                     | 서브 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"              |
| subcaption-font-size     | Float                                  | 0.6     | em                  | 서브 캡션의 글꼴 크기.                                                                 |
| subcaption-font-weight   | normal / bold                          | normal  |                     | 서브 캡션의 글꼴 가중치.                                                                |
| subcaption-font-style    | normal / italic                        | normal  |                     | 서브 캡션의 글꼴 스타일.                                                                |
| subcaption-font-no-scale | Boolean                                | no      |                     | 서브 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                           |
| caption-align            | left / right / center                  | left    |                     | 캡션과 서브 캡션의 텍스트 정렬 방식.                                                         |
| caption-height           | Float                                  | 0       | dp, em, layout의 상대값 | 캡션 영역의 높이.                                                                    |
| inner-caption            | Boolean                                | no      |                     | 캡션 영역을 이미지 영역 안으로 배치하려면 yes를 지정한다.                                            |
| caption-color            | Color                                  | #000000 |                     | 캡션의 글자색.                                                                      |
| subcaption-color         | Color                                  | #000000 |                     | 서브 캡션의 글자색.                                                                   |
| caption-background-color | Color                                  | 투명      |                     | 캡션 영역의 배경색.                                                                   |

#### 액션 <a href="#_75" id="_75"></a>

| 액션    | 매개변수                             | 설명              |
| ----- | -------------------------------- | --------------- |
| play  |                                  | 비디오를 재생함.       |
| pause |                                  | 비디오를 일시 정지함.    |
| stop  |                                  | 비디오를 정지함.       |
| seek  | time={재생할 위치의 시간 값, 00:00:00 형식} | 비디오 재생 위치를 변경함. |

#### 이벤트 <a href="#_76" id="_76"></a>

| 이벤트 액션명              | 설명                   |
| -------------------- | -------------------- |
| action-when-finished | 비디오 재생이 완료되었을 때 발생함. |

### 웹비디오 (Web Video) <a href="#web-video" id="web-video"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_77" id="_77"></a>

```
=object webvideo: url="https://embed-ssl.ted.com/talks/shivani_siroya_a_smart_loan_for_people_with_no_credit_history_yet.html"
```

#### 속성 <a href="#_78" id="_78"></a>

| 속성                       | 타입(허용값)                                | 기본값     | 단위                  | 설명                                                                            |
| ------------------------ | -------------------------------------- | ------- | ------------------- | ----------------------------------------------------------------------------- |
| url                      | URL                                    | None    |                     | 비디오의 URL.                                                                     |
| autoplay                 | Boolean                                | no      |                     | 오브젝트가 활성화될 때 자동으로 비디오를 재생하려면 yes를 지정한다.                                       |
| loop                     | Boolean                                | no      |                     | 비디오를 반복하여 재생하려면 yes를 지정한다.                                                    |
| control-hidden           | Boolean                                | no      |                     | 비디오 제어 창을 숨기려면 yes를 지정한다.                                                     |
| info-hidden              | Boolean                                | no      |                     | 비디오 정보를 숨기려면 yes를 지정한다.                                                       |
| preview-image            | 파일명                                    | None    |                     | 비디오가 재생되기 전에 나타날 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                         |
| image-downloadable       | Boolean                                | no      |                     | 이미지를 외부에서 다운로드할 수 있을 때 yes로 지정한다.                                             |
| caption                  | String                                 | None    |                     | 비디오의 캡션.                                                                      |
| subcaption               | String                                 | None    |                     | 비디오의 서브 캡션.                                                                   |
| caption-font             | "\[weight] \[style] size family"       |         |                     | 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"    |
| caption-font-family      | serif / sans-serif / monospace / 글꼴 이름 | serif   |                     | 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                 |
| caption-font-size        | Float                                  | 0.8     | em                  | 캡션의 글꼴 크기.                                                                    |
| caption-font-weight      | normal / bold                          | normal  |                     | 캡션의 글꼴 가중치.                                                                   |
| caption-font-style       | normal / italic                        | normal  |                     | 캡션의 글꼴 스타일.                                                                   |
| caption-font-no-scale    | Boolean                                | no      |                     | 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                              |
| subcaption-font          | "\[weight] \[style] size family"       |         |                     | 서브 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace" |
| subcaption-font-family   | serif / sans-serif / monospace / 글꼴 이름 | serif   |                     | 서브 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"              |
| subcaption-font-size     | Float                                  | 0.6     | em                  | 서브 캡션의 글꼴 크기.                                                                 |
| subcaption-font-weight   | normal / bold                          | normal  |                     | 서브 캡션의 글꼴 가중치.                                                                |
| subcaption-font-style    | normal / italic                        | normal  |                     | 서브 캡션의 글꼴 스타일.                                                                |
| subcaption-font-no-scale | Boolean                                | no      |                     | 서브 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                           |
| caption-align            | left / right / center                  | left    |                     | 캡션과 서브 캡션의 텍스트 정렬 방식.                                                         |
| caption-height           | Float                                  | 0       | dp, em, layout의 상대값 | 캡션 영역의 높이.                                                                    |
| inner-caption            | Boolean                                | no      |                     | 캡션 영역을 이미지 영역 안으로 배치하려면 yes를 지정한다.                                            |
| caption-color            | Color                                  | #000000 |                     | 캡션의 글자색.                                                                      |
| subcaption-color         | Color                                  | #000000 |                     | 서브 캡션의 글자색.                                                                   |
| caption-background-color | Color                                  | 투명      |                     | 캡션 영역의 배경색.                                                                   |

#### 액션 <a href="#_79" id="_79"></a>

| 액션    | 매개변수                             | 설명               |
| ----- | -------------------------------- | ---------------- |
| play  |                                  | 비디오를 재생한다.       |
| pause |                                  | 비디오를 일시 정지한다.    |
| stop  |                                  | 비디오를 정지한다.       |
| seek  | time={재생할 위치의 시간 값, 00:00:00 형식} | 비디오 재생 위치를 변경한다. |

#### 이벤트 <a href="#_80" id="_80"></a>

| 이벤트 액션명              | 설명                   |
| -------------------- | -------------------- |
| action-when-finished | 비디오 재생이 완료되었을 때 발생함. |

### 유튜브 (YouTube) <a href="#youtube" id="youtube"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_81" id="_81"></a>

```
=object youtube: video-id="9bZkp7q19f0"
```

#### 속성 <a href="#_82" id="_82"></a>

| 속성                       | 타입(허용값)                                | 기본값     | 단위                  | 설명                                                                            |
| ------------------------ | -------------------------------------- | ------- | ------------------- | ----------------------------------------------------------------------------- |
| video-id                 | String                                 | None    |                     | 유튜브 비디오의 ID.                                                                  |
| autoplay                 | Boolean                                | no      |                     | 오브젝트가 활성화될 때 자동으로 비디오를 재생하려면 yes를 지정한다.                                       |
| loop                     | Boolean                                | no      |                     | 비디오를 반복하여 재생하려면 yes를 지정한다.                                                    |
| plays-inline             | Boolean                                | yes     |                     | 비디오 재생시 전체 화면으로 확대하려면 no를 지정한다.                                               |
| control-hidden           | Boolean                                | no      |                     | 비디오 제어 창을 숨기려면 yes를 지정한다.                                                     |
| info-hidden              | Boolean                                | no      |                     | 비디오 정보를 숨기려면 yes를 지정한다.                                                       |
| shows-related            | Boolean                                | yes     |                     | 비디오의 재생이 끝난 뒤, 화면에 관련 동영상이 나타나지 않게 하려면 no를 지정한다.                              |
| preview-image            | 파일명                                    | None    |                     | 비디오가 재생되기 전에 나타날 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                         |
| image-downloadable       | Boolean                                | no      |                     | 이미지를 외부에서 다운로드할 수 있을 때 yes로 지정한다.                                             |
| caption                  | String                                 | None    |                     | 비디오의 캡션.                                                                      |
| subcaption               | String                                 | None    |                     | 비디오의 서브 캡션.                                                                   |
| caption-font             | "\[weight] \[style] size family"       |         |                     | 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"    |
| caption-font-family      | serif / sans-serif / monospace / 글꼴 이름 | serif   |                     | 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                 |
| caption-font-size        | Float                                  | 0.8     | em                  | 캡션의 글꼴 크기.                                                                    |
| caption-font-weight      | normal / bold                          | normal  |                     | 캡션의 글꼴 가중치.                                                                   |
| caption-font-style       | normal / italic                        | normal  |                     | 캡션의 글꼴 스타일.                                                                   |
| caption-font-no-scale    | Boolean                                | no      |                     | 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                              |
| subcaption-font          | "\[weight] \[style] size family"       |         |                     | 서브 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace" |
| subcaption-font-family   | serif / sans-serif / monospace / 글꼴 이름 | serif   |                     | 서브 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"              |
| subcaption-font-size     | Float                                  | 0.6     | em                  | 서브 캡션의 글꼴 크기.                                                                 |
| subcaption-font-weight   | normal / bold                          | normal  |                     | 서브 캡션의 글꼴 가중치.                                                                |
| subcaption-font-style    | normal / italic                        | normal  |                     | 서브 캡션의 글꼴 스타일.                                                                |
| subcaption-font-no-scale | Boolean                                | no      |                     | 서브 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                           |
| caption-align            | left / right / center                  | left    |                     | 캡션과 서브 캡션의 텍스트 정렬 방식.                                                         |
| caption-height           | Float                                  | 0       | dp, em, layout의 상대값 | 캡션 영역의 높이.                                                                    |
| inner-caption            | Boolean                                | no      |                     | 캡션 영역을 이미지 영역 안으로 배치하려면 yes를 지정한다.                                            |
| caption-color            | Color                                  | #000000 |                     | 캡션의 글자색.                                                                      |
| subcaption-color         | Color                                  | #000000 |                     | 서브 캡션의 글자색.                                                                   |
| caption-background-color | Color                                  | 투명      |                     | 캡션 영역의 배경색.                                                                   |

#### 액션 <a href="#_83" id="_83"></a>

| 액션    | 매개변수                             | 설명               |
| ----- | -------------------------------- | ---------------- |
| play  |                                  | 비디오를 재생한다.       |
| pause |                                  | 비디오를 일시 정지한다.    |
| stop  |                                  | 비디오를 정지한다.       |
| seek  | time={재생할 위치의 시간 값, 00:00:00 형식} | 비디오 재생 위치를 변경한다. |

#### 이벤트 <a href="#_84" id="_84"></a>

| 이벤트 액션명              | 설명                   |
| -------------------- | -------------------- |
| action-when-finished | 비디오 재생이 완료되었을 때 발생함. |

### 비메오 (Vimeo) <a href="#vimeo" id="vimeo"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_85" id="_85"></a>

```
=object vimeo: video-id="176434092"
```

#### 속성 <a href="#_86" id="_86"></a>

| 속성                       | 타입(허용값)                                | 기본값     | 단위                  | 설명                                                                            |
| ------------------------ | -------------------------------------- | ------- | ------------------- | ----------------------------------------------------------------------------- |
| video-id                 | String                                 | None    |                     | 비메오 비디오의 ID.                                                                  |
| autoplay                 | Boolean                                | no      |                     | 오브젝트가 활성화될 때 자동으로 비디오를 재생하려면 yes를 지정한다.                                       |
| loop                     | Boolean                                | no      |                     | 비디오를 반복하여 재생하려면 yes를 지정한다.                                                    |
| control-hidden           | Boolean                                | no      |                     | 비디오 제어 창을 숨기려면 yes를 지정한다.                                                     |
| info-hidden              | Boolean                                | no      |                     | 비디오 정보를 숨기려면 yes를 지정한다.                                                       |
| preview-image            | 파일명                                    | None    |                     | 비디오가 재생되기 전에 나타날 이미지의 파일명. 파일은 Images 디렉토리에 들어있어야 한다.                         |
| image-downloadable       | Boolean                                | no      |                     | 이미지를 외부에서 다운로드할 수 있을 때 yes로 지정한다.                                             |
| caption                  | String                                 | None    |                     | 비디오의 캡션.                                                                      |
| subcaption               | String                                 | None    |                     | 비디오의 서브 캡션.                                                                   |
| caption-font             | "\[weight] \[style] size family"       |         |                     | 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace"    |
| caption-font-family      | serif / sans-serif / monospace / 글꼴 이름 | serif   |                     | 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"                 |
| caption-font-size        | Float                                  | 0.8     | em                  | 캡션의 글꼴 크기.                                                                    |
| caption-font-weight      | normal / bold                          | normal  |                     | 캡션의 글꼴 가중치.                                                                   |
| caption-font-style       | normal / italic                        | normal  |                     | 캡션의 글꼴 스타일.                                                                   |
| caption-font-no-scale    | Boolean                                | no      |                     | 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                              |
| subcaption-font          | "\[weight] \[style] size family"       |         |                     | 서브 캡션의 글꼴. weight, style 은 생략 가능. 예) "bold 1.2em sans-serif", "0.7 monospace" |
| subcaption-font-family   | serif / sans-serif / monospace / 글꼴 이름 | serif   |                     | 서브 캡션의 글꼴 종류. 콤마(,)로 구분하여 여러 값 입력 가능. 예) "맑은 고딕, 굴림, sans-serif"              |
| subcaption-font-size     | Float                                  | 0.6     | em                  | 서브 캡션의 글꼴 크기.                                                                 |
| subcaption-font-weight   | normal / bold                          | normal  |                     | 서브 캡션의 글꼴 가중치.                                                                |
| subcaption-font-style    | normal / italic                        | normal  |                     | 서브 캡션의 글꼴 스타일.                                                                |
| subcaption-font-no-scale | Boolean                                | no      |                     | 서브 캡션의 글꼴 크기가 사용자의 글꼴 크기 설정에 영향을 받지 않으려면 yes로 지정한다.                           |
| caption-align            | left / right / center                  | left    |                     | 캡션과 서브 캡션의 텍스트 정렬 방식.                                                         |
| caption-height           | Float                                  | 0       | dp, em, layout의 상대값 | 캡션 영역의 높이.                                                                    |
| inner-caption            | Boolean                                | no      |                     | 캡션 영역을 이미지 영역 안으로 배치하려면 yes를 지정한다.                                            |
| caption-color            | Color                                  | #000000 |                     | 캡션의 글자색.                                                                      |
| subcaption-color         | Color                                  | #000000 |                     | 서브 캡션의 글자색.                                                                   |
| caption-background-color | Color                                  | 투명      |                     | 캡션 영역의 배경색.                                                                   |

#### 액션 <a href="#_87" id="_87"></a>

| 액션    | 매개변수                             | 설명               |
| ----- | -------------------------------- | ---------------- |
| play  |                                  | 비디오를 재생한다.       |
| pause |                                  | 비디오를 일시 정지한다.    |
| stop  |                                  | 비디오를 정지한다.       |
| seek  | time={재생할 위치의 시간 값, 00:00:00 형식} | 비디오 재생 위치를 변경한다. |

#### 이벤트 <a href="#_88" id="_88"></a>

| 이벤트 액션명              | 설명                   |
| -------------------- | -------------------- |
| action-when-finished | 비디오 재생이 완료되었을 때 발생함. |

### 웹 (Web) <a href="#web" id="web"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_89" id="_89"></a>

```
=object web: url="http://m.naver.com"
```

#### 속성 <a href="#_90" id="_90"></a>

| 속성                | 타입(허용값) | 기본값  | 단위 | 설명                                         |
| ----------------- | ------- | ---- | -- | ------------------------------------------ |
| filename          | 파일명     | None |    | 웹페이지 파일명. 파일은 루트 디렉토리에 들어있어야 한다.           |
| url               | URL     | None |    | 웹페이지의 URL.                                 |
| bounces           | Boolean | yes  |    | 웹페이지의 바운스 효과를 허용하지 않으려면 yes를 지정한다.         |
| loads-when-appear | Boolean | no   |    | 오브젝트가 활성화되지 않더라도 웹페이지를 즉시 로드하려면 yes를 지정한다. |

#### 액션 <a href="#_91" id="_91"></a>

#### 이벤트 <a href="#_92" id="_92"></a>

### PDF 페이지 (PDF Page) <a href="#pdf-pdf-page" id="pdf-pdf-page"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_93" id="_93"></a>

```
=object pdf: url="http://www.pdf.org / sample.pdf", page=1
```

#### 속성 <a href="#_94" id="_94"></a>

| 속성       | 타입(허용값) | 기본값  | 단위 | 설명                                    |
| -------- | ------- | ---- | -- | ------------------------------------- |
| filename | 파일명     | None |    | pdf의 파일명. 파일은 루트 디렉토리에 들어있어야 한다.      |
| url      | URL     | None |    | pdf 파일의 URL.                          |
| page     | Integer | 1    |    | pdf의 페이지 번호.                          |
| bounces  | Boolean | yes  |    | pdf 페이지의 바운스 효과를 허용하지 않으려면 yes를 지정한다. |

#### 액션 <a href="#_95" id="_95"></a>

N/A

#### 이벤트 <a href="#_96" id="_96"></a>

N/A

### 차트 (Chart) <a href="#chart" id="chart"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_97" id="_97"></a>

```
=object chart: filename="chart.json"
```

#### 속성 <a href="#_98" id="_98"></a>

| 속성       | 타입(허용값) | 기본값  | 단위 | 설명                                                                                                                                     |
| -------- | ------- | ---- | -- | -------------------------------------------------------------------------------------------------------------------------------------- |
| filename | 파일명     | None |    | 차트 데이터의 파일명. 파일은 Texts 디렉토리에 들어있어야 한다. 파일 포맷은 json이며 데이터에 대한 자세한 설명은 [http://www.chartjs.org/docs](http://www.chartjs.org/docs)를 참조한다. |

#### 액션 <a href="#_99" id="_99"></a>

N/A

#### 이벤트 <a href="#_100" id="_100"></a>

N/A

### 빈 영역 (Blank) <a href="#blank" id="blank"></a>

* 지원 플랫폼: iOS, 안드로이드
* 잼킷 버전: 1.0

#### 사용예 <a href="#_101" id="_101"></a>

```
=object blank: color="#ff0"
```

#### 속성 <a href="#_102" id="_102"></a>

| 속성    | 타입(허용값) | 기본값 | 단위 | 설명           |
| ----- | ------- | --- | -- | ------------ |
| color | Color   | 투명  |    | 빈 영역을 채울 색상. |

#### 액션 <a href="#_103" id="_103"></a>

N/A

#### 이벤트 <a href="#_104" id="_104"></a>

N/A
