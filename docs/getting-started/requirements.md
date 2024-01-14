---
title: 개발 환경 요구 사양
description: Jamkit 개발 환경에 대해 소개하고 요구 사양을 알아봅니다.
---

# Jamkit 개발 환경 요구 사양

Jamkit은 Node.js를 기반으로 개발 환경을 제공합니다. 따라서 Windows, macOS 등 어디서든 쉽게 모바일 앱을 개발할 수 있습니다.

## 개발 환경에 맞는 디바이스 준비하기

Jamkit을 이용하여 앱을 개발하기 위해서는 다음의 조건을 만족하는 디바이스를 갖추는 것이 좋습니다.

### 개발자 PC의 경우

* 인텔, AMD 등 64비트 코드를 실행할 수 있는 최신 프로세서를 탑재한 노트북 또는 데스크톱
* Windows 10 Pro 22H2 이상 또는 Windows 11 Pro 23H2 이상의 운영 체제
* 최소 8GiB 이상의 메모리와 16GiB 이상의 여유 공간이 확보된 SSD (하드 디스크는 권장하지 않음)
* 블루투스 5.0, USB 3.0, Wi-Fi 2.4GHz 이상의 유선 및 무선 네트워크 프로토콜 지원 필요

### 개발자 Mac의 경우

* Apple Silicon M1 및 그 이후에 출시된 프로세서를 탑재한 Mac 랩탑 또는 데스크탑
* macOS 12 Monterey 이상의 운영 체제

## 테스트 디바이스 준비하기

효율적인 앱 개발을 위해 별도의 테스트용 디바이스를 통해 앱을 개발하는 것을 권장합니다. 다음의 조건을 만족하는 디바이스를 갖추는 것을 권장합니다.

### 테스트용 Android 폰의 경우

* Android 10 (API 레벨 29) 이상의 OS를 실행하는 Android 스마트폰
    * 개발 환경을 구축할 PC의 OS가 Windows인 경우, 해당 테스트용 Android 폰 제조사가 AMD64 (x64) 버전 USB 드라이버를 Windows 10 및 그 이후 OS용으로 제공하는지 확인해야 합니다. ([관련 내용 살펴보기](https://developer.android.com/studio/run/oem-usb))

### 테스트용 iPhone의 경우

* iOS 15 이상의 OS를 실행하는 iPhone

## 개발 환경에 맞는 소프트웨어 및 기타 항목 준비하기

* Node.js 개발 환경을 지원하는 IDE나 코드 편집기 사용을 권장합니다.
    * 여러 소프트웨어가 있지만, Jamkit은 Visual Studio Code를 사용하여 개발하는 것을 권장합니다.

* 앱을 출시하려는 OS의 종류를 확인하여 사전 요구 사항을 미리 준비합니다.
    * Android용 앱을 개발하는 경우, Android Studio 및 Android SDK를 설치하고 실행해야 합니다.
    * iOS용 앱을 개발하는 경우, Xcode 앱을 설치하고, Apple Developer Membership에 가입하여 앱 스토어에 앱을 출시할 수 있는 라이선스를 획득해야 합니다.
