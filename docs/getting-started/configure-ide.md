---
title: IDE 환경 설정하기
description: Jamkit 개발 환경을 설정하기 위한 자세한 방법을 안내합니다.
---

## Visual Studio Code

Jamkit은 기본적으로 Visual Studio Code를 이용하여 앱을 개발합니다.

1. [Visual Studio Code 홈페이지](https://code.visualstudio.com/download)에서 OS에 맞는 Visual Studio Code 최신 버전을 설치합니다.
1. Jamkit Syntax Highlight 플러그인을 다운로드합니다.
   [VSIX 파일 다운로드하기](https://github.com/bookjam/jamkit-developer-guide/raw/gitbook/vscode-jamkit-0.2.1.vsix)
1. Visual Studio Code 실행 후, **확장** - *...* - **VSIX에서 설치**를 눌러 다운로드한 VSIX 파일을 열어 설치를 진행합니다.
1. 만약 Visual Studio Code 다시 로드 버튼이 표시되면, 다시 로드 버튼을 눌러 프로그램을 다시 실행합니다.

## Android Studio 환경 설정

Jamkit을 이용하여 Android 앱을 개발할 때에는 Android SDK 플랫폼 도구를 설치하고 구성해야 합니다. 다음의 순서를 따라서 최신 버전의 Android SDK 플랫폼 도구를 설치하고 구성할 수 있습니다.

1. [Android Studio 홈페이지](https://developer.android.com/studio?hl=ko)에서 OS에 맞는 Android Studio 최신 버전을 설치합니다.

1. Android Studio 설치를 마치고 실행한 다음, `Tools` - `SDK Manager` - `SDK Tools` 메뉴로 이동하여 **Android SDK Platform - Tools**를 설치합니다.
   ![](images/android-studio-sdk-platform-tools.png)

1. 사용 중인 OS에 맞는 방법으로 Android SDK 플랫폼 도구가 자동으로 인식될 수 있게 환경 변수를 맞춥니다.

    === "Windows"
        1. "내 컴퓨터" 창을 열고, 빈 공간에서 마우스 오른쪽 버튼을 클릭합니다.
        1. `속성` - `고급 시스템 설정` - `환경 변수` - 상단의 `사용자 변수` 항목을 찾습니다.
        1. `PATH` 항목을 찾아 선택한 후, **편집** 버튼을 클릭합니다.
        1. 새로운 환경 변수 항목을 만들고, `%localappdata%\Android\Sdk\Platform-tools` 항목을 입력한 후 저장합니다.
        1. 만약 목록 형태가 아닌 한 줄로 표시되는 창이 나타날 경우, 이렇게 추가할 수 있습니다.
          1. 값 부분의 제일 마지막 글자를 봅니다.
          1. 제일 마지막 글자가 세미콜론으로 끝나지 않으면 세미콜론 `;` 문자를 하나 넣습니다.
          1. 그 다음, `%localappdata%\Android\Sdk\Platform-tools`를 입력하고 저장합니다.

    === "macOS"
        1. 터미널을 열고, `echo $SHELL` 명령어를 실행하여 지금 어떤 셸을 실행하고 있는지 확인합니다. 대개 zsh인 경우가 많습니다. 만약 zsh나 bash 셸이 아닌 다른 셸인 경우, 해당 셸의 환경 변수 설정 방법을 참고하여 `PATH` 환경 변수를 편집할 수 있는 단계로 진입합니다.
        1. zsh 셸인 경우 `vi ~/.zshrc` 명령어를 입력하고, bash 셸인 경우 `vi ~/.bash_profile` 명령어를 입력합니다.
        1. `a` 키를 눌러 삽입 모드로 진입합니다.
        1. 제일 아랫줄로 이동하여 `export PATH=$PATH:{SDK경로}/platform-tools/` 내용을 입력합니다. 이 때, `{SDK 경로}` 부분은 Android Studio에서 **Android Studio** - **Tools** - **SDK Manager** - **Android SDK Location**에서 확인할 수 있습니다. 대개 `/Users/{사용자명}/Library/Android/sdk`인 경우가 많습니다.
        1. ESC키를 눌러 삽입 모드를 종료하고, `:wq` 입력 후 Enter 키를 누르면 파일 내용이 저장됨과 동시에 vi 편집기가 종료됩니다.
        1. 터미널 창을 종료한 후 다시 실행합니다.

<!-- To Do: adb로 안드로이드 디바이스와 연결이 잘 되는지까지 확인하는 내용 추가가 필요할 지 검토 필요 -->
