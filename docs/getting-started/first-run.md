---
description: Jamkit 개발 환경이 잘 설치되었는지 확인하기 위해, 첫 앱을 만들고 실행해봅니다.
---

# 첫 Jamkit 앱 만들고 실행해보기

첫 번째 프로젝트로 "Hello World" 앱을 만들고 실행해보겠습니다. 안드로이드 기기 또는 에뮬레이터(안드로이드, iOS)에서 앱을 실행할 수 있습니다.

### 안드로이드 기기에서 실행하기

#### 유선 연결 설정

1. USB 케이블로 기기와 PC를 연결합니다.
2. 기기의 USB 디버깅을 활성화합니다.
   1. **설정** 앱을 엽니다.
   2. 하단으로 스크롤하여 **휴대전화 정보**를 선택합니다.
   3. **소프트웨어 정보**를 선택합니다.
   4. **빌드번호**를 7번 탭합니다.
   5. **설정** 화면으로 돌아가서 하단으로 스크롤하여 **개발자 옵션**을 선택합니다.
   6. 하단으로 스크롤하여 **USB 디버깅**을 활성화합니다.

#### 무선 연결 설정

1. Android Studio의 **Device Manager** 창을 열고 **Physical** 탭을 선택합니다.
2. Pair using Wi-Fi를 클릭합니다.
3. 기기의 무선 디버깅을 활성화합니다.
   1. **설정** 앱을 엽니다.
   2. 하단으로 스크롤하여 **휴대전화 정보**를 선택합니다.
   3. **소프트웨어 정보**를 선택합니다.
   4. **빌드번호**를 7번 탭합니다.
   5. **설정** 화면으로 돌아가서 하단으로 스크롤하여 **개발자 옵션**을 선택합니다.
   6. 하단으로 스크롤하여 **무선 디버깅**을 활성화합니다.
4. 무선 디버깅 메뉴를 탭하여 진입 후, 페어링합니다.
   1. **QR 코드로 기기 페어링**을 선택하고, Android Studio에 표시된 QR 코드를 인식합니다. (QR 코드로 한번 페어링한 기기는, 이후 **무선 디버깅**을 활성화하기만 해도 연결됩니다.)
   2. **페어링 코드로 기기 페어링**을 선택하고, Android Studio에 검색된 기기를 페어링합니다.

#### 잼킷을 실행합니다.

1. Visual Studio Code를 실행합니다.
2. 툴바의 "메뉴 > 터미널 > 새 터미널" 또는 "Ctrl + \`"로 터미널 창을 엽니다.
3. 아래 명령어를 입력합니다.

```
jamkit create HelloWorld // 샘플 프로젝트 생성
cd HelloWorld // 프로젝트 폴더로 이동
jamkit run // jamkit 최초 실행 시, jamkit 슈퍼 앱 설치
jamkit run // HelloWorld 앱 실행

macOS에서는 아래 명령어를 실행한다.
jamkit run --platform=android
```

### Android Studio 에뮬레이터에서 실행하기

#### 아래에 따라 에뮬레이터를 실행합니다.

1. Android Studio를 실행합니다.
2. Virtual Device Manager를 실행합니다.
   1. 우측 상단 **...** 메뉴를 클릭하여 **Virtual Device Manager**를 선택합니다.
   2. 좌측 상하 **Create device**를 선택합니다.
   3. **디바이스 해상도 선택화면**에서 기본 선택된 Pixel 5를 확인하고 Next 버튼을 클릭합니다.
   4. **시스템 이미지 선택화면**에서 S(Android 12)를 선택하고 다운로드 후, Next 버튼을 클릭합니다.
   5. 디바이스 이름을 입력하고(안 해도 무방) Finish 버튼을 클릭합니다.
   6. Device Manager 창에서 Actions 메뉴의 Play 버튼을 클릭합니다.

#### 잼킷을 실행합니다.

1. Visual Studio Code를 실행합니다.
2. 툴바의 "메뉴 > 터미널 > 새 터미널" 또는 "Ctrl + \`"로 터미널 창을 엽니다.
3. 아래 명령어를 입력합니다.

```bash
jamkit create HelloWorld // 샘플 프로젝트 생성
cd HelloWorld // 프로젝트 폴더로 이동
jamkit run // jamkit 최초 실행 시, jamkit 슈퍼 앱 설치
jamkit run // HelloWorld 앱 실행

macOS에서는 아래 명령어를 실행한다.
jamkit run --platform=android
```
