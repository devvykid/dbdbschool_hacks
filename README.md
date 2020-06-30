# dbdbschool_hacks

dbdbschool 시스템의 다양한 script hack을 모아놓은 레포입니다.
[여기](https://github.com/Seia-Soto/EnrolmentMacro-YoungilMS2019S2)에서 포크하였습니다.

- 해당 로그인 매크로는 모든 dbdbschool 기반 로그인 폼에서 작동합니다. (학생 전용)

## 사용법

**하기 전에 [신청사이트에 접속](https://www.dbdbschool.kr/member/login/sn/1088)한 뒤 반드시 F12 키로 개발자 도구를 열고 [Console] 탭으로 이동하세요.**

- [그냥 한 번에 다 하기](#justOnce)

1. 아래를 전체 복사한 후에 콘솔에 붙여넣은 후에 [Enter] 키를 누르세요.

```js
var selectors = {
  form: 'form#fm_edit',
  gradeDropdown: 'select#login_stu_grade',
  classDropdown: 'select#login_stu_class',
  numberDropdown: 'select#login_stu_bunho',
  nameInput: 'input#login_stu_name',
  passwordInput: 'input#login_stu_passwd',
  submitButton: 'input[name="submit"]',
  formTitle: 'span.s_name'
}

function fillForm(source) {
  $(selectors.gradeDropdown).val(source.grade)
  $(selectors.classDropdown).val(source.class)
  $(selectors.numberDropdown).val(source.number)
  $(selectors.nameInput).val(source.name)
  $(selectors.passwordInput).val(source.password)
}
function submitForm() {
  $(selectors.submitButton).click()
}

function login_stu(source) {
  setTimeout(function() {
    fillForm(source)
    submitForm(source)
  }, new Date('July 13, 2019 08:00:00').getTime() - new Date().getTime())
  setInterval(function() {
    var timeLeft = new Date('July 13, 2019 08:00:00').getTime() - new Date().getTime()

    var hours = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
    var minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60))
    var seconds = Math.floor((timeLeft % (1000 * 60)) / 1000)

    $(selectors.formTitle).text(
      hours + '시간 ' + minutes + '분 ' + seconds + '초 뒤에 자동으로 로그인'
    )
  }, 1000)
}
```

2. 아래를 전체 복사한 후에 적절히 수정하여 콘솔에 붙여넣은 후에 [Enter] 키를 누르세요.

_**아래 내용을 적절하게 수정하세요**_

```js
var source = {
  grade: 0/* 학년 */, // NOTE: 학년
  class: 0/* 반 */, // NOTE: 반
  number: 0/* 번 */, // NOTE: 번호
  name: `이름`, // NOTE: 이름, "`" 기호를 지우지 마세요.
  password: `비밀번호` // NOTE: 비밀번호, "`" 기호를 지우지 마세요.
}

// NOTE: 입력한 내용 삭제:
console.clear()
```

3. 아래 내용 전체를 복사하고 붙여넣은 뒤에 [Enter] 키를 누른 후에 **시간이 되면** 자동으로 로그인됩니다.

```js
login_stu(source)

// NOTE: 개인정보를 포함한 변수 삭제
delete source
```

## justOnce

```js
var selectors={form:"form#fm_edit",gradeDropdown:"select#login_stu_grade",classDropdown:"select#login_stu_class",numberDropdown:"select#login_stu_bunho",nameInput:"input#login_stu_name",passwordInput:"input#login_stu_passwd",submitButton:'input[name="submit"]',formTitle:"span.s_name"};function fillForm(e){$(selectors.gradeDropdown).val(e.grade),$(selectors.classDropdown).val(e.class),$(selectors.numberDropdown).val(e.number),$(selectors.nameInput).val(e.name),$(selectors.passwordInput).val(e.password)}function submitForm(){$(selectors.submitButton).click()}function login_stu(e){setTimeout(function(){fillForm(e),submitForm(e)},new Date("July 13, 2019 08:00:00").getTime()-(new Date).getTime()),setInterval(function(){var e=new Date("July 13, 2019 08:00:00").getTime()-(new Date).getTime(),t=Math.floor(e%864e5/36e5),o=Math.floor(e%36e5/6e4),s=Math.floor(e%6e4/1e3);$(selectors.formTitle).text(t+"시간 "+o+"분 "+s+"초 뒤에 자동으로 로그인")},1e3)}

login_stu({
  grade: 0/* 학년 */, // NOTE: 학년
  class: 0/* 반 */, // NOTE: 반
  number: 0/* 번 */, // NOTE: 번호
  name: `이름`, // NOTE: 이름, "`" 기호를 지우지 마세요.
  password: `비밀번호` // NOTE: 비밀번호, "`" 기호를 지우지 마세요.
})

// NOTE: 입력한 내용 삭제:
console.clear()
```
