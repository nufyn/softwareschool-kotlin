# Visibility 속성
- invisible = 원래 있던 공간을 차지하면서 안보이게 되는 것
- gone = 공간마저 없애버리는 것


# TextView의 속성

- textStyle = normal, bold, italic
-textColor = #FF0000 (16진수 RGB포맷)
- testSize = 16dp 폰트 사이즈
- autoLink= web, email, phone 텍스트를 자동으로 웹링크 연결, 메일, 전화 연결할 수 있게 해줌
- maxLines = 최대 줄 수
- ellipsize 최대 줄 수 지정으로 같지만 줄임표시(...)


# ImageView의 속성
- src = 어떤 이미지를 보여줄 것인지
- XML에선 android:src = "@drawable/sample"와 같이 지정
- adjustViewBounds = 길어서 어려워보이는데 결국 가로세로 비율 유지할건지
- tint = 이미지에 다른 색상을 입힐 때 사용

# EditText의 속성
- lines = 보여지는 줄 수 (3이면 세 줄만큼만 보인다. 안의 내용이 3줄 이상이면 스크롤됨)
- maxLines = 3 (처음 보일 때 한줄로보이지만 세 줄만큼 늘어남 마찬가지로 스크롤)
- inputType = 사용자의 키패드를 어떻게 할것인지
  - none: 모든 문자 입력 가능
  - textPassword: 비밀번호 입력용 (점으로 표시되는 거)
  - number: 숫자 입력 가능
  - numberPassword: 비밀번호 입력용 (점표시, 숫자만)
- gravity 텍스트 편집 할 때 어디로 정렬할 건지 (기본: left top)

# CheckBox
- CheckBox는 여러 개 체크 가능한 것
- isChecked = true / false

# RadioButton
- RadioGroup중에서 한 개만 체크 가능
- check() = RadioButton의 id를 전달하면 해당 버튼이 체크됨
- clearCheck = 모든 체크 상태 해제
- getCheckedRadioButtonId = 현재 체크된 RadioButton의 id를 return