# Jamkit 명령어 도구

### Create

create는 프로젝트를 생성하는 명령어입니다.

#### 기본 명령어

아래 명령어를 실행하면 HelloWorld 템플릿이 생성됩니다.

```
jamkit create {프로젝트명}
```

#### 옵션

`--template`: 다른 템플릿으로 앱을 생성하려는 경우

```
jamkit create --template=XXX
```

### Run

run은 기기나 에뮬레이터에서 앱을 실행하는 명령어입니다.

#### 기본 명령어

```
jamkit run
```

#### 옵션

\--platform=android: macOS에서 실행할 경우

```
jamkit run --platform=android
```

\--skip-sync: 파일을 기기나 에뮬레이터로 복사하지 않고 바로 실행

```
jamkit run --skip-sync
```

\--mode=jam: 슈퍼앱이 실행 중인 상태에 미니앱 실행

```
jamkit run --mode=jam
```

### Build

build는 앱 패키지를 생성하는 명령어입니다.

#### 기본 명령어

```
jamkit build
```

#### 옵션

```
```

### Install

install은 앱 패키지를 기기에 설치하는 명령어입니다.

#### 기본 명령

```
jamkit install
```

#### 옵션

```
```

### Publish

publish는 앱 패키지를 IPFS에 업로드하여 공유할 수 있게 해주는 명령어입니다.

#### 기본 명령어

```
jamkit publish
```

#### 옵션

```
```

### Generate

generate는 MS 엑셀 파일에서 데이터베이스를 생성하는 명령어입니다.

#### 기본 명령어

```
jamkit generate {엑셀 파일명}
```

#### 옵션

```
```
