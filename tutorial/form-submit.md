# 사용자 입력 데이터 다루기

### form

사용자가 입력하는 내용을 한꺼번에 가져오는 방식입니다. 보통 sbml 내에 form section을 만들고, 내부에 사용자가 입력할 수 있는 object를 나열합니다.

object에 입력된 데이터는 key\&value 쌍으로 이루어진 딕셔너리가 되어 저장, 전송, 스크립트 처리할 수 있습니다.

{% code overflow="wrap" %}
```javascript
// sbml
=begin XXX: form={id}
=object textfield: id=title 
=object checkbox: id=check
...
=end XXX
```
{% endcode %}

section의 form id와 object의 form id를 통일하고, script={scirpt name}으로 설정하면, 해당 object에 입력된 데이터가 해당 script로 넘어갑니다.

사용자가 입력하지 않은, 개발자가 원하는 데이터를 parameter로 전달하고 싶을 때는 input object를 쓰면 됩니다.

{% code overflow="wrap" %}
```javascript
// sbml
=begin XXX: form=abc
=object textfield: id=title, script=on_form, form=abc
=object input: id=acd, value=kyc
=end XXX
```
{% endcode %}

#### validation

사용자가 입력한 데이터가 적합한지 validation할 수 있습니다. jamkit 자체에서 처리하거나, 스크립트에서 처리할 수 있습니다.

form validation의 기본 속성은 meesage-when-<mark style="color:red;">invalid</mark>, action-when-<mark style="color:red;">invalid</mark>, script-when-<mark style="color:red;">invalid</mark> 형태입니다. textfield는 empty 상태가 특수한 속성이어서 \~\~\~-when-<mark style="color:red;">empty</mark> 형태로 속성이 부여되어 있습니다.

* textfield

| 속성                 | 값                             | 설명                                                                          |
| ------------------ | ----------------------------- | --------------------------------------------------------------------------- |
| invalid-when-empty | yes                           | 비어 있으면 invalid 처리                                                           |
| message-when-empty |                               | invalid 상태일 때, 얼럿으로 띄울 메시지                                                  |
| action-when-empty  | none / toast / alert / script | invalid 상태일 때, 메시지를 toast나 alert으로 띄우거나 script를 실행함                         |
| script-when-empty  | {script name}                 | <p>invalid 상태일 때, script를 실행함<br>💡 action-when-empty=none or script 필요</p> |

| 속성                    | 값     | 설명                                                                 |
| --------------------- | ----- | ------------------------------------------------------------------ |
| valid-format          | email | 입력값이 email 형태가 아니면 invalid 처리                                      |
| valid-format          | 정규표현식 | 전화번호나 비밀번호 등 다양한 조건을 구현할 수 있음                                      |
| prevents-invalid-text | yes   | <p>valid한 텍스트만 입력받을 수 있음<br>💡 중간 단계의 valid-format을 모두 허용해줘야 함</p> |

```javascript
// 기본
=object textfield: id=title, invalid-when-empty=yes, \
                message-when-empty="타이틀을 작성하세요!", \
                action-when-empty=toast, \
                valid-format=email
                
// script
=object textfield: id=title, invalid-when-empty=yes, \
                message-when-empty="타이틀을 작성하세요!", \
                action-when-empty="none", \
                script-when-empty="on_error", \

// valid-format
=object textfield: id=author, \
                valid-format="[0-9]{3}", \
                message-when-invalid="invalid text!", \
                action-when-invalid="none", \
                script-when-invalid="on_error", \
                prevents-invalid-text=yes
```

* checkbox

| 속성                   | 값      | 설명                                                             |
| -------------------- | ------ | -------------------------------------------------------------- |
| group                |        | 함께 동작해야 하는 checkbox를 동일한 group으로 묶음                            |
| value                |        | 각 checkbox마다 별개의 value를 지정함                                    |
| select-mode          | single | group 내에 check가 하나만 유지됨                                        |
| valid-when-selected  | yes    | <p>check하지 않았을 때 invalid 처리<br>💡 필수로 체크해야 하는 checkbox에 설정</p> |
| message-when-invalid |        | invalid 상태일 때, alert으로 띄울 메시지                                  |
| action-when-invalid  | toast  | invalid 상태일 때, 메시지를 toast로 띄움                                  |

{% code overflow="wrap" %}
```javascript
// sbml
=(object checkbox: group=check, value=checked1, style=btn_check)= \
=(object checkbox: group=check, value=checked2, style=btn_check)= \
=(object checkbox: group=check, value=checked3, style=btn_check)=

// sbss
#btn_check: width=50dp, margin-top=50dp, \
            image="uncheck.png", selected-image="check.png", \
            select-mode=single, \
            valid-when-selected=yes, message-when-invalid="check!", \
            action-when-invalid="toast"
```
{% endcode %}

### submit

submit은 로컬 sqlite에 데이터를 저장하는 액션입니다.&#x20;

* action-when-xxx=submit
* params-when-xxx="form={id}, showcase=data, display-unit=S\_123"\
  data라는 showcase에 있는 S\_123이라는 id로 데이터를 만들거나, id가 이미 있으면 데이터를 추가한다.\
  동일한 key가 있으면 해당 key의 value를 덮어쓴다.

| 속성               | 값                  | 설명                     |
| ---------------- | ------------------ | ---------------------- |
| action-when-done | bottom-sheet-close | submit이 완료되면 액션을 실행함   |
| script-when-done |                    | submit이 완료되면 스크립트를 실행함 |

{% code overflow="wrap" %}
```javascript
// sbml
=begin title: form=message
=object textfield: id=title, invalid-when-empty=no, \
                   message-when-empty="타이틀을 작성하세요!", placeholder=title, \
                   action-when-empty="none", script-when-empty=on_error, \
                   style=txt_message
=object textfield: id=word, style=txt_message, placeholder=word
=end title

=object button: action=submit, params="form=message, showcase=alphabet, \
                display-unit=S_MY_APPS_${TIMESTAMP}", \
                script=on_form, form=message, style=btn_done, \
                action-when-done="bottom-sheet-close", \
                script-when-done=on_done
```
{% endcode %}

submit으로 데이터를 url로 보낼 수도 있습니다.

* params-when-xxx="form={id}, url={url}"
