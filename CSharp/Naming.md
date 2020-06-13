# C# Naming Convention

## 주석 지침
* 코드 줄의 끝이 아닌 별도의 줄에 주석을 배치합니다
```C#
# BAD
if(val1 > var2) // 조건검색.

# GOOD
// 조건검색.
if(val1 > var2)
```
* 주석을 영어로 작성할 경우 <b>대문자</b>로 시작한다
* 주석 끝에는 <b>마침표</b>를 붙인다
* 주석 구분 기호(//)와 주석 사이에 <b>공백</b>을 삽입한다

## 레이아웃 규칙
* 기본적으로 들여쓰기는 <b>탭 하나(공백 4개)</b>로 지정한다
* 선언과, 문은 한줄에 하나만 작성한다
* Method 정의와 속성정의 간에는 빈 줄을 하나 이상 추가한다
* 괄호를 이용하여 식의 절을 명확히 구분한다

```C#
int val1 = 10;
int val2 = 20;

public bool CheckEqual(int a, int b){
    if((a != 0 && b != 0) && a != b){
        return false;
    } else {
        return true;
    }
}

```
## 변수명
```
PascalCase : 첫단어를 대문자로 시작하는 표기
camelCase : 각 단어의 첫문자를 대문자로 표기하고 붙여쓰되, 맨 처음 문자는 소문자로 표기
Hungarian notation : 자료형 + 변수명
```
* <b>Hungarian notation</b>을 사용하지 않는다
* 그 대신, 변수가 담는 내용을 표현하는데 중심을 둔다
``` C#
# BAD
int iVal;
bool _fail;

# GOOD
int val;
bool isFail;
```

* Class와 Method, Delegate, Event 명은 <b>PascalCase</b>을 사용한다
* Method Arguments, 변수에는 <b>camelCase</b>을 사용한다


* 맴버 필드에 대해 접두어(prefix)를 붙이지 않는다
    * 지역변수에 _ 문자를 사용하지 않는다
    * 맴버변수는 _로 시작해, 지역변수와 구분되게 작명한다

    클래스 멤버들을 명시적으로 표시하기 위해 멤버 앞에 this. 를 사용한다
    ```C#
    private int _age;
    public Person(int age){
    # BAD
        this.age = age;
    # GOOD
        this._age = age;
    }
    ```




* Method는 행위를 나타내므로 동사(verb)를 이용한다
```C#
# BAD
public int Addition(int a, int b);

# GOOD
public int Add(int a, int b);
```


* 필드나 속성 혹은 변수는 명사(noun)를 사용한다
```C#
# BAD
private bool createTable  //나쁜 표현

# GOOD
private bool newTable  //좋은 표현
```


boolean 형의 변수/필드는 is, has, can 등의 접두어를 붙여서 사용한다
```C#
# BAD
private bool bSuccess;

# GOOD
private bool isSuccess;
```

이벤트는 가능하면 동사형으로 표현한다
```C#
# BAD
public event EventHandler Completion;

# GOOD
public event EventHandler Completed;
```

클래스명, enum명, 대리자(delegate)명에는 어떤 Prefix도 붙이지 않는다
```C#
# BAD
public enum ENotiType {};

# GOOD
public enum NotificationType {};
```

클래스명, 메서드명, 속성명 등의 명칭에 축약된 단어를 사용하지 않는다
```C#
# BAD
public int GetNoti();

# GOOD
public int GetNotification();
```

* 꼭 필요하거나 널리 알려진 용어는 축약형을 사용할 수 있다
    * 예시 : UserInterface -> UI
    * 축약형을 사용할 경우에는 두글자까지는 모두 대문자로, <br> 두글자 초과인 경우는 <b>PascalCase</b>이나<b>camelCase</b>을 사용한다
``` C#
# BAD
HTMLButton
System.Io

# GOOD
HtmlButton
System.IO
```

* 인터페이스는 I로 시작한다
```C#
public interface INotification { }
```

* 되도록 한글자로 이루어진 변수를 사용하지 않는다
    * 가능다면 의미있는 단어로 사용한다
```C#
# BAD
for(int i = 0; i < list.Count; i++)

# GOOD
for(int idx = 0; idx < list.Count; idx++)
```


* Generics 클래스의 Generic 파라미터 타입은 가능하면 T와 같이 한 문자를 선택한다
    * 단, 복수 타입의 파라메터를 받는경우, 예외한다
```C#
# BAD
public class MyArray<TValue>{}

# GOOD
public class MyArray<T>{}
public class MyArray<TValue, KValue>{}
public class MyArray<T, K>{}
```

* 변수명을 예약어와 유사하게 사용하지 않는다

* 파일명은 해당 클래스명으로 사용한다
* 파일명은 <b>PascalCase</b>을 사용한다


* UI 구성요소에 대해서 알맞은 접두어를 붙여서 다른 변수와 구분하라




### 참조
[공식 코딩 컨벤션](https://docs.microsoft.com/ko-kr/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)<br>
[CSharpStudy](http://www.csharpstudy.com/Guide/Guide-naming.aspx)
