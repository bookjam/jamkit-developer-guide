# 멀티 컨텍스트 스크립트 엔진

### 컴포넌트의 스크립트 컨텍스트는 독립적입니다

![](images/multi-context.png)

* 각 컴포넌트는 자신만의 스크립트 컨텍스트를 가지고 있습니다.
* 스크립트의 컨텍스트가 모두 독립적이기 때문에 모듈별 개발이 용이합니다.
* SBML/SBSS 역시 독립적인 네임 스페이스를 가지고 있습니다.
