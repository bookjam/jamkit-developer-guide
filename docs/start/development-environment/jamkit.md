# Jamkit

### Jamkit 설치하기

#### PowerShell(Window)이나 터미널(macOS)에서 아래의 명령어를 실행하여 Jamkit을 설치합니다.

```
[Windows]
npm install -g jamkit

[macOS] 관리자 권한으로 실행
sudo npm install -g jamkit
```

![](images/npm-install-jamkit.png)

#### (Windows만 해당) PowerShell에서 아래의 명령어를 실행하여 실행규칙을 변경합니다.

```
Set-ExecutionPolicy Unrestricted
```

![](images/windows-powershell-run-policy.png)

{% hint style="warning" %}
**설치 중 에러 발생 시, 대처방법**

* gyp 에러 시, Python 경로 설정
  * Windows: npm config set python C:\Python310\python.exe
  * macOS: npm config set python /usr/bin/python3

*   xcode license 에러 시, license 동의

    * macOS: sudo xcodebuild -license

    <img src="images/xcode-license-error.png" alt="" data-size="line">
{% endhint %}
