# C# Language GuideLine


## 문자열
* 되도록 문자열은 리소스파일에 저장해라
* 짧은 문자열을 연결할때는, 아래 샘플과 같이 <b>문자열 보간</b>을 사용한다
``` C#
string name = $"{peopleList[n].Name}({peopleList[n].Age})";
```

* 많은 양의 텍스트를 사용할때, 문자열을 반복문에 추가하려면 <b>StringBuilder</b> 개체를 사용한다

``` C#
var phrase = "testetsetsetsetes";
var str = new StringBuilder();
for (var i = 0; i < 100; i++) {
    str.Append(phrase);
}
//Console.WriteLine("str : " + str);
```

## 지역변수
* 중요한 숫자의 경우 const, readonly를 이용해 상수화 해라
* 할당한 변수가 형식이 명확하거나, 형식이 중요하지 않다면, <b>암시적 형식</b>을 사용한다
```C#
var var1 = "This is clearly a string.";
var var2 = 27;
var var3 = Convert.ToInt32(Console.ReadLine());
var var4 = true;
```
* 변수이름에 변수 형식을 지정하지 않습니다. 형식이 올바르지 않을 수 있습니다
``` C#
// BAD CASE
var inputInt = Console.ReadLine();
Console.WriteLine(inputInt);
```

* dynamic 대신 var를 사용하지 않습니다

* for 루프의 루프 변수 형식은 암시적 형식을 사용합니다
``` C#
var phrase = "testetsetsetsetes";
var str = new StringBuilder();
for (var i = 0; i < 100; i++) {
    str.Append(phrase);
}
//Console.WriteLine("str : " + str);
```

* foreach 루프의 루프 변수 형식을 결정하기 암시적 형식을 사용하지 않습니다
```C#
foreach (char ch in laugh) {
    if (ch == 't') {
        Console.Write("T");
    } else {
        Console.Write(ch);
    }
}
Console.WriteLine();
```

## 반복문
* 반복할때, continue나 break가 필요한 경우 되도록 최상위에 적도록 한다
```C#
foreach(int score in scoreList) {
    if (score < 0) {
        continue;
    }
    if (score == 100) {
        break;
    }
    doSomething();
}
```
## 부호 없는 데이터 형식
* 일반적으로는 부호 없는 형식 대신 int를 사용한다
``` C#
# BAD
uint test = 0;

# GOOD
int test = 0;
```

## 배열
* 선언에서 배열을 초기화할 때는 간결한 구문을 사용한다

```C#
// 이상적인 배열 선언방법
string[] array1 = { "a", "e", "i", "o", "u" };

// 명시적인 인스턴스화를 할 경우 var를 사용할 수 있다
var array2 = new string[] { "a", "e", "i", "o", "u" };

// 배열 사이즈를 지정한다면, 한번에 하나씩 요소를 초기화 해야한다
var array3 = new string[4];
array3[0] = "t";
array3[1] = "e";
```

## Delegate
* Delegate 인스턴스를 만들려면 간결한 구문을 사용한다
```C#
public delegate void Del(string message);

public static void DelMethod(string str) {
    Console.WriteLine("DelMethod argument: {0}", str);
}

// Del exampleDel2 = new Del(DelMethod);
Del exampleDel2 = DelMethod;
```

## 조건 처리
* 조건 실패시, return 하는 경우, 최상단에서 처리하도록 한다
```C#
if(age < 0){
    return;
}

doSomething();
```

## 예외 처리의 try-catch 및 using 문
```C#
try {
    return array[index];
} catch (System.IndexOutOfRangeException ex) {
    Console.WriteLine("Index is out of range: {0}", index);
    throw;
}
```
* 만약 try-finally 문이 존재하고, finally 블록의 코드가 Dispose() 호출인 경우에는 using으로 대신 사용한다

```C#

Font font1 = new Font("Arial", 10.0f);
try {
    byte charset = font1.GdiCharSet;
} finally {
    if (font1 != null) {
        ((IDisposable)font1).Dispose();
    }
}

using (Font font2 = new Font("Arial", 10.0f)) {
    byte charset = font2.GdiCharSet;
}
```

## && 및 || 연산자
* 예외를 방지하고 불필요한 비교를 건널려면, & 대신 &&, | 대신 ||을 사용한다
* &, |은 비트연산이 필요할때만 사용한다


## New 연산자
* 암시적 형식이 포함된 간결한 형태의 개체 인스턴스화를 사용한다

```C# 
var instance1 = new PeopleClass();

var instance2 = new PeopleClass { Name = "test", Age = 15, Gender = "Male"};

var instance3 = new PeopleClass();
instance4.Name = "test";
instance4.Age = 15;
instance4.Gender = "Male";
```

## 이벤트 처리
* 나중에 제거할 필요가 없는 이벤트는 <b>람다 식</b>을 사용한다
```C#
# BAD
public Form1() {
    this.Click += new EventHandler(Form1_Click);
}

void Form1_Click(object sender, EventArgs e) {
    MessageBox.Show(((MouseEventArgs)e).Location.ToString());
}

# GOOD
public Form2() {
    this.Click += (s, e) => {
        MessageBox.Show(((MouseEventArgs)e).Location.ToString());
    };
}
```

### 참조
[C# 공식문서](https://docs.microsoft.com/ko-kr/dotnet/csharp/programming-guide/inside-a-program/coding-conventions#language-guidelines)