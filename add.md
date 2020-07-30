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



# TableLayOut
```xml
<TableLayout
        android:id="@+id/chart"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:stretchColumns="*"
        app:layout_constraintTop_toBottomOf="@id/tab1"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:padding="3dp"
        android:layout_margin="5dp"
        tools:ignore="MissingConstraints">
        <TableRow
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginBottom="3dp"
            >
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="40dp"
                android:layout_marginRight="3dp"
                android:text="성분이름"
                android:textSize="15sp"
                android:gravity="center"
                />
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="40dp"
                android:layout_marginRight="3dp"
                android:text="성분비율"
                android:textSize="15sp"
                android:gravity="center"
                />
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="40dp"
                android:layout_marginRight="3dp"
                android:text="DM(수분제외 %)"
                android:textSize="15sp"
                android:gravity="center"
                />
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="40dp"
                android:text="비고"
                android:textSize="15sp"
                android:gravity="center"
                />
        </TableRow>

        <TableRow
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginBottom="3dp"
            >
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="30dp"
                android:layout_marginRight="3dp"
                android:text=""
                android:textSize="13sp"
                android:gravity="center"
                />

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="30dp"
                android:layout_marginRight="3dp"
                android:gravity="center"
                android:text=""
                android:textSize="13sp" />
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="30dp"
                android:layout_marginRight="3dp"
                android:text=""
                android:textSize="13sp"
                android:gravity="center"
                />
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="30dp"
                android:text=""
                android:textSize="13sp"
                android:gravity="center"
                />
        </TableRow>
    </TableLayout>
```


# StartActivityForResult
## FirstActivity
```kotlin
var REQUEST_TEST = 1
button.setOnClickListener(){
            
    var intent = Intent(this, SecondActivity::class.java)
    startActivityForResult(intent, REQUEST_TEST)
}
```

## SecondActivity
```kotlin
    var intent = Intent()
    intent.putExtra("result", "some value")
    setResult(RESULT_OK, intent)
    finish()
```

## FirstActivity
```kotlin
override fun onActivityResult(requestCode: Int, resultCode: Int, data: Intent?) {
        super.onActivityResult(requestCode, resultCode, data)
        if (requestCode == REQUEST_TEST) {
            if (resultCode == RESULT_OK) {
                data!!.getStringExtra("result")
            } else { 
                Toast.makeText(this, "Failed", Toast.LENGTH_SHORT).show()
            }
        }
    }
```
# Logcat
```kotlin
Log.d("태그", "내용 : "+a)
```
```
2020-07-30 06:03:52.752 6763-6763/com.example.example D/태그: 내용 : 111
```
  * date : 날짜
  * time : 시간
  * PID : 프로세스 아이디
  * TID : 쓰레드 아이디
  * pakage : 클래스의 패키지
  * priority : 우선 순위 - V(Verbose) < D(Debug) < I(Info) < W(Warning) < E(Error) < A(Assert)
  * tag : 메소드의 첫번째 인자인 TAG 입니다.
  * message : 메소드의 두 번째 인자인 message 입니다.

# Toast
```kotiln
    Toast.makeText(this, "토스트 메세지 띄우기 입니다.", Toast.LENGTH_SHORT).show()
```
# SnackBar
## build.gradle(Module: app)
```gradle
dependencies {
    implementation 'com.android.support:design:2x.0.0'
}
```

```
val actionSnackbar = Snackbar.make(layout, "Hello World", LENGTH_INDEFINITE)
```
- view = 뷰를 지정하여야 하며, Snackbar는 Snackbar를 화면에 보여줄 수 있도록 해당 view의 부모 view를 찾음
- text = 문자열
- duration = LENGTH_LONG, LENGTH_SHORT, LENGTH_INDEFINITE, Toast 와 다르게 직접 8000(8초)라고 입력해서 원하는 시간만큼 보여주는 것도 가능
## MainActivity.kt
```kotlin
fun showActionSnackbar(){
        val actionSnackbar = Snackbar.make(layout, "Hello World", LENGTH_INDEFINITE)
        actionSnackbar.setAction("눌러") {
            Toast.makeText(this, "확인 누름!", Toast.LENGTH_LONG).show()
        }
        actionSnackbar.show()
    }
```

# Dialog
```kotlin
var dialog = AlertDialog.Builder(this)
            dialog.setTitle("첫 다이얼로그 시도")
            dialog.setMessage("첫 다이얼로그의 본문텍스트 영역입니다.")
            dialog.setIcon(R.mipmap.ic_launcher)
            fun toast_p() {
                Toast.makeText(this, "Positive 버튼을 눌렀습니다.", Toast.LENGTH_SHORT).show()
            }
            fun toast_n(){
                Toast.makeText(this, "Negative 버튼을 눌렀습니다.", Toast.LENGTH_SHORT).show()
            }
            var dialog_listener = object: DialogInterface.OnClickListener{
                override fun onClick(dialog: DialogInterface?, which: Int) {
                    when(which){
                        DialogInterface.BUTTON_POSITIVE ->
                            toast_p()
                        DialogInterface.BUTTON_NEGATIVE ->
                            toast_n()
                    }
                }
            }

            dialog.setPositiveButton("YES",dialog_listener)
            dialog.setNegativeButton("NO",dialog_listener)
            dialog.setNeutralButton("Cancel", null)
            dialog.show()
```
# Font
[폰트다운로드](https://noonnu.cc/)
## 1. 폰트 파일의 이름을 소문자로 변경
## 2. R/font 생성
## 3. R/font에 폰트추가
## 4. R/font/font.xml 생성
```xml
<?xml version="1.0" encoding="utf-8"?>
<font-family xmlns:android="http://schemas.android.com/apk/res/android">
    <font
        android:fontStyle = "normal"
        android:fontWeight = "400"
        android:font = "@font/nanum"/>
</font-family>
```


# Button Style 
## 1. Drawable 폴더에 New -> Drawable Resource File을 선택한다.
## 2. 원하는 파일명 설정

```kotlin
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
</selector>
```
## 3. 위의 코드 <selector> 태그안에 뷰의 디자인을 구성한다.
 - shape : 모양
 - solid : 내부 색상
 - stroke : 테두리 두께 및 색상 설정
 - corners : 테두리의 둥근 정도를 설정
 - 이외에도 많은 것들이 있지만 대표적인 것으로만 예를 듬


<br>

- rounded_button.xml
 ```xml
 <?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item>
        <shape
            android:shape="rectangle"   >

            <solid
                android:color="@color/colorPrimary" >
            </solid>

            <stroke
                android:width="1dp"
                android:color="@color/colorPrimary" >
            </stroke>

            <corners
                android:radius="10dp"   >
            </corners>

        </shape>
    </item>
</selector>
```

뷰의 디자인 파일을 만들고 버튼이 있는 xml의 버튼의 속성으로 
android:background = "@drawable/파일명"
 적용시켜주면 디자인이 적용된 버튼을 볼 수 있다.

 # Fragment
- 카카오톡을 예시로 들어보자 하단의 친구, 채팅, #, 설정 탭이 있다. 근데 이 탭을 누를 때에 액티비티가 전환되는 것이 아니고 일부 영역만 화면이 전환 되는 것이다.

- 하단에 탭의 역할을 하는 뷰는 BottomNavigationView로 이루어 지고 화면은 FrameLayout이라는 뷰로 이루어진다.

- BottomNavigationView를 사용할려면 해당 패키지를 다운받아야 하는데 xml 디자인탭에서 BottomNavigationView를 검색하면 위젯하나가 나오는데 옆의 다운로드 버튼을 통해 다운로드를 하면된다.

- 하단의 친구, 채팅, #, 설정을 메뉴의 아이템으로 관리가 된다. (밑의 코드 참조)

<br>
<br>
 
- activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <com.google.android.material.bottomnavigation.BottomNavigationView
        android:id="@+id/bnv_main"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="#FFFFFF"
        app:menu="@menu/menu_bnv"
        app:labelVisibilityMode="labeled"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

    <FrameLayout
        android:id="@+id/frame_main"
        android:layout_width="0dp"
        android:layout_height="0dp"
        app:layout_constraintBottom_toTopOf="@+id/bnv_main"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent">

    </FrameLayout>
</androidx.constraintlayout.widget.ConstraintLayout>
```

- fragment_first.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".FirstFragment">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="첫번째 화면 입니다 !"
        android:textSize="50dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
- menu_bnv.xml(res폴더에 New->Android Resource Directory->Resource Type : menu 생성)
```xml
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:id="@+id/bnv_main_home"
        android:title="Home"
        />

    <item
        android:id="@+id/bnv_main_category"
        android:title="카테고리"
        />

    <item
        android:id="@+id/bnv_main_mypage"
        android:title="내정보"
        />

    <item
        android:id="@+id/bnv_main_message"
        android:title="메시지"
        />
</menu>
```

- MainActivity.kt
```kotlin
if (savedInstanceState == null) {
    val firstFragment = FirstFragment()
    supportFragmentManager.beginTransaction().replace(R.id.frame_main, firstFragment).commit()
}

bnv_main.setOnNavigationItemSelectedListener {
    when(it.itemId) {
        R.id.bnv_main_home -> {
            val firstFragment = FirstFragment()
            supportFragmentManager.beginTransaction().replace(R.id.frame_main, firstFragment).commit()
            return@setOnNavigationItemSelectedListener true
         }
        R.id.bnv_main_category -> {
            val secondFragment = SecondFragment()
            supportFragmentManager.beginTransaction().replace(R.id.frame_main, secondFragment).commit()
            return@setOnNavigationItemSelectedListener true
        }
        R.id.bnv_main_message -> {
            val thirdFragment = ThirdFragment()
            supportFragmentManager.beginTransaction().replace(R.id.frame_main, thirdFragment).commit()
            return@setOnNavigationItemSelectedListener true
        }
        R.id.bnv_main_mypage -> {
            val fourthFragment = FourthFragment()
            supportFragmentManager.beginTransaction().replace(R.id.frame_main, fourthFragment).commit()
            return@setOnNavigationItemSelectedListener true
        }
    }
    false
}
```


# Drawer 
- 카카오톡을 예시로 들어보자 채팅방에서 우측위 상단 메뉴버튼을 누르면 오른쪽에서 화면이 삽입되기 시작하는데 이것을 DrawerLayout이라고 한다.
- DrawerLayout을 사용하기 위해 NavigationView를 사용해야 하는데 위의 BottomNavigationView와 같은 방법으로 패키지를 다운받는다.
- DrawerLayout에 들어가는 버튼들 (ex) 카카오톡 DrawerLayout의 톡게시판, 사진동영상 등)들 또한 메뉴의 아이템으로 관리된다.
<br>
<br>

- res -> layout -> drawer.xml 생성
- drawer.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.drawerlayout.widget.DrawerLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/drawer_layout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    <include
        layout="@layout/activity_main"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

    <com.google.android.material.navigation.NavigationView
        android:id="@+id/naviation_view"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:menu="@menu/menu_drawer"
        android:layout_gravity="start"
        android:fitsSystemWindows="true"/>

</androidx.drawerlayout.widget.DrawerLayout>

``` 

- menu_drawer.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <group
        android:id="@+id/group_home">
        <item android:title="Home">
            <menu>
                <item
                    android:id="@+id/test1"
                    android:title="Test1"
                    />
                <item
                    android:id="@+id/test2"
                    android:title="Test2"/>
                <item
                    android:id="@+id/test3"
                    android:title="Test3"/>
            </menu>
        </item>

    </group>
</menu>
```

- MainActivity.kt
```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.drawer)

        var drawerLayout : DrawerLayout = findViewById(R.id.drawer_layout)
        var navigationView : NavigationView = findViewById(R.id.naviation_view)


        navigationView.setNavigationItemSelectedListener {
            when (it.itemId) {
                R.id.test1 -> {
                    drawer_layout.closeDrawers()
                }
                R.id.test2 -> {

                }
                R.id.test3 -> {

                }
            }
            false
        }

        btn_open.setOnClickListener {
            if(!drawerLayout.isDrawerOpen(GravityCompat.START))
                drawerLayout.openDrawer(GravityCompat.START)
        }
    }
```
