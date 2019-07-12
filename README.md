# EnrolmentMacro-YoungilMS2019S2

dbdbschool 기반 영일중학교 자유학기제 수강신청 로그인 매크로

- 해당 로그인 매크로는 모든 dbdbschool 기반 로그인 폼에서 작동합니다. (학생 전용)

## 사용법

1. 아래를 전체 복사한 후에 콘솔에 붙여넣은 후에 [Enter] 키를 누르세요.

```js
var selectors = {
  form: 'form#fm_edit',
  gradeDropdown: 'select#login_stu_grade',
  classDropdown: 'select#login_stu_class',
  numberDropdown: 'select#login_stu_bunho',
  nameInput: 'input#login_stu_name',
  passwordInput: 'input#login_stu_passwd',
  submitButton: 'input[name="submit"]'
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

function login_stu() {
  fillForm(source)
  submitForm()
}
```

2. 아래를 전체 복사한 후에 적절히 수정하여 콘솔에 붙여넣은 후에 [Enter] 키를 누르세요.

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

3. 아래 내용 전체를 복사하고 붙여넣은 뒤에 **시간이 되면** [Enter] 키를 누르면 자동으로 로그인됩니다.

_**아래 내용을 적절하게 수정하세요**_

```js
login_stu()

// NOTE: 개인정보를 포함한 변수 삭제
delete source
```
