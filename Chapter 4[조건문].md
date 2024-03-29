### 4. 조건문
#### - 학습 목표
> **1.** 프로그램에서 분기를 만들 수 있다.
> **2.** 열거형을 사용할 수 있다.
> **3.** 논리 연산자를 응용할 수 있다.
---
#### - 조건문

게임이나 앱을 실행하다보면 사용자로부터 입력을 받는 창을 본 적이 있을 것이다. 가령 '종료하시겠습니까? (y/n)' 같은 것들 말이다. **조건문**(conditional statement)은 프로그램에게 분기를 제공하게 해주는 구문이다. C++의 조건문에는 `if`, `else`, 삼항 연산자`(?:)`, `switch`로 네 가지가 있다. 자세히 알아보자.

- `if`
> <center> if (조건) 구문; </center>

`if` 구문의 문법은 이렇다. `if`를 쓰고 괄호 안에 조건을 써준다. 이 때의 조건은 `true`거나 `false`일 수 있는 `bool`형이다. 조건이 참이라면 구문을 실행하게 된다. 예제를 확인해보자.

```c++
//if 예제 - 1
#include <stdio.h>

int main()
{
  printf("1~100까지의 숫자를 입력해주세요. : ");
  int num;
  scanf("%d", &num);
  if (num >= 50)
    puts("입력한 숫자는 50이상입니다.");

  return 0;
}
```

어떻게 동작하는지 직관적으로 알 수 있을 것이다. 그러나 다음과 같은 예제는 원하는 대로 동작하지 않는다.

```c++
//if 예제 - 2
#include <stdio.h>

int main()
{
  printf("1~100까지의 숫자를 입력해주세요. : ");
  int num;
  scanf("%d", &num);
  if (num >= 50)
    puts("입력한 숫자는 50이상입니다.");
    puts("굉장히 높은 숫자군요.");

  return 0;
}
```

50 미만의 숫자를 입력했음에도 두 번째 `puts()`가 실행 되었다. 이를 통해 `if`문은 조건이 참일 시 바로 다음 구문만 실행한다는 것을 알 수 있을 것이다. 그럼, 여러 구문을 동작하는 방법이 없을까? 아니다. 있다. 바로, 블록을 쓰는 것이다.

```c++
//if 예제 - 3
#include <stdio.h>

int main()
{
  printf("1~100까지의 숫자를 입력해주세요. : ");
  int num;
  scanf("%d", &num);
  if (num >= 50)
  {
    puts("입력한 숫자는 50이상입니다.");
    puts("굉장히 높은 숫자군요.");
  }

  return 0;
}
```

이제는 분명히 원하는 대로 동작한다. 구문이 하나이던, 여러 개이던 블록을 넣어주는 것이 좋다. 후의 코드를 수정할 때에도 실수를 방지할 수 있기 때문이다.

- `else`
> <center> else 구문; </center>

`if`문으로 내는 분기는 두 방향이다. 하나는 '그렇거나'(if), 다른 하나는 '그렇지 않거나'. 후자를 담당하는 부분이 `else`문이다. 그렇기 때문에, 단독으로 쓰일 수 없고, 꼭 `if`문과 같이 붙어야 한다.

```c++
//else 예제 - 1
#include <stdio.h>

int main()
{
  printf("1~100까지의 숫자를 입력해주세요. : ");
  int num;
  scanf("%d", &num);
  if (num >= 50)
  {
    puts("입력한 숫자는 50이상입니다.");
    puts("굉장히 높은 숫자군요.");
  }
  else //else도 if의 특성을 닮고 있다.
  {
    puts("에게, 숫자가 너무 작네요.");
  }

  return 0;
}
```

이미 결과를 예상한 사람들도 있을 것 같다. 주의해야 할 것은 `else`는 가장 가까이 있는 `if`와 붙는다. 즉, 다음처럼 쓴다고 기대하는 바대로 결과가 나오진 않는다.

```c++
if (boolean)
  ... //Blah Blah
  if (boolean)
    ... //Blah Blah
else                //두번째 if문과 붙음
  ... //Blah Blah
```

주의하자.

- `?:`(삼항 연산자)
> <center> 조건 ? 참일 때 구문 : 거짓일 때 구문; </center>

단순히 `if else`로 끝나는 분기라면 삼항 연산자로 한번에 쓸 수 있다.

```c++
//삼항 연산자 예제 - 1
#include <stdio.h>

int main()
{
  printf("1~100까지의 숫자를 입력해주세요. : ");
  int num;
  scanf("%d", &num);
  (num >= 50) ?
        puts("입력한 숫자는 50이상입니다.") :
              puts("에게, 숫자가 너무 작네요.");

  return 0;
}
```

하지만, 구문이 길다면 가독성이 떨어지기에, 비교적 간단한 구문에만 쓰이곤 한다.<small>(그렇다고 긴 구문에 완전히 안 쓰인다고 말하는 것은 아니다.)</small> 긴 구문을 쓴다면 위에 나와있는 것과 같이 들여쓰기를 이용해 잘 정리를 해줘야 할 것이다.

자 그럼 분기를 여러 방향으로 내볼 순 없을까? 이렇게 쓰면 가능하다. `else` 문에 `if`문을 연달아 쓰는 것이다. 즉, '그렇지 않거나'에 또 다른 조건을 붙여주는 것이다.

```c++
//else 예제 - 2
#include <stdio.h>

int main()
{
  printf("1~100까지의 숫자를 입력해주세요. : ");
  int num;
  scanf("%d", &num);
  if (num >= 50)
  {
    puts("입력한 숫자는 50이상입니다.");
    puts("굉장히 높은 숫자군요.");
  }
  else if (num >= 30)
  {
    puts("그래도 준수하네요.");
  }
  else
  {
    puts("에게, 너무 작네요.");
  }

  return 0;
}
```

이제 여러 방향으로 분기를 낼 수 있게 되었다. 자, 그럼 이것을 토대로 숫자를 10단위로 잘라보자. 어떤가? 귀찮고 가독성도 뛰어나지 않아 보인다. 이럴 때 쓸 수 있는 것이 `switch`문이다.

- `switch`
<blockquote>
  <center>
  switch ( 표현식 )
  </center>
  <center>  
  case 상수표현식 : 구문
  </center>
  <center>  
  [default  : 구문]  
  </center>
</blockquote>

앞서 나열한 것들 보다 뭔가 복잡해 보이지만, 당황하지 말고 차근차근 보자.

우선 표현식에는 정수가 들어간다. int형 변수나, 정수 리터럴, int로 명시적 변환된 것들이 있다. `switch`는 `case` 레이블과 짝 지어지는데, 이 `case` 레이블에는 상수 표현식이 들어간다. 표현식에 들어간 값이 해당 `case` 레이블과 일치할시 구문이 실행된다. `default` 레이블은 써도 되고 안써도 되지만, 되도록 쓰는 것을 권장한다. 어떠한 `case`에도 속하지 않을 시, 이 레이블이 실행된다.

백문이 불여일견. 직접 한번 보자.

```c++
//switch 예제 - 1
#include <stdio.h>

int main()
{
  printf("1~100까지의 숫자를 입력해주세요. : ");
  int num;
  scanf("%d", &num);
  switch (num / 10)
  {
    case 10: puts("100 이네요!");
    case 9:  puts("90번대네요!");
    case 8:  puts("80번대네요!");
    case 7:  puts("70번대네요!");
    case 6:  puts("60번대네요!");
    case 5:  puts("50번대네요!");
    case 4:  puts("40번대네요!");
    case 3:  puts("30번대네요!");
    case 2:  puts("20번대네요!");
    case 1:  puts("10번대네요!");
    default: puts("범위를 넘어선 수에요.");
  }

  return 0;
}
```

여러분이 쓴 `if else`구문보다 훨씬 보기가 편하고 깔끔해보인다. 그럼 실행해보자. 결과가 어떤가? 이상한 결과가 뜨지 않는가?

왜 일까? 하나 빠뜨렸기 때문이다. 바로 `break`문이다. 해당 레이블로 이동한 후에는 '제동'을 걸어주지 않으면 중괄호 가드레일을 만나기 전까지 그냥 달려버린다. 따라서, `break`문을 쓰는 습관을 들이자. 물론 이 특성을 이용해서 다음과 같은 것도 가능하다.
<!--- fallthrough--->

```c++
//switch 예제 - 2
#include <stdio.h>

int main()
{
  printf("시험 점수를 입력해주세요.(만점 100점) : ");
  int num;
  scanf("%d", &num);
  switch (num / 10)
  {
    case 10: case 9:
      puts("당신의 학점은 A입니다.");
      break;
    case 8: case 7: case 6:
      puts("당신의 학점은 B입니다.");
      break;
    case 5: case 4:
      puts("당신의 학점은 C입니다.");
      break;
    case 3: case 2:
      puts("당신의 학점은 D입니다.");
      break;
    case 1:
      puts("당신의 인생, 아, 아니 학점은 F입니다.");
      break;
    default:
      puts("이상한 거 입력하지 마세요.");
      break;
  }

  return 0;
}
```

이해가 되는가? 비슷한 군끼리 묶은 것이다. 이렇듯 `switch`문은 형식이 균일하며 처리해야 할 조건이 많을 때 유용하다. 모든 분기문을 `switch`로 고칠 순 없겠지만, 분기가 많고 변환이 가능하다면 적극 사용해보자.

자 그럼 여기서, 리터럴을 되도록 사용하지 말자고 했던 걸 기억하는가? 대신 기호상수를 쓰는 것이 낫다고 하였다. 그럼 기호 상수로 고쳐보자.

```c++
//switch 예제 - 3
#include <stdio.h>

#define GRADE_A 10
#define GRADE_B 9
#define GRADE_C 8
#define GRADE_D 7
#define GRADE_F 6

int main()
{
  printf("시험 점수를 입력해주세요.(만점 100점) : ");
  int num;
  scanf("%d", &num);
  switch (num / 10) {
    case GRADE_A:
      puts("당신의 학점은 A입니다.");
      break;
    case GRADE_B:
      puts("당신의 학점은 B입니다.");
      break;
    case GRADE_C:
      puts("당신의 학점은 C입니다.");
      break;
    case GRADE_D:
      puts("당신의 학점은 D입니다.");
      break;
    case GRADE_F:
      puts("당신의 학점은 F입니다.");
      break;
    default:
      puts("이상한 거 입력하지 마세요.");
      break;
  }

  return 0;
}
```

조금 더 의미는 와 닿는다. 그럼 이걸 의미론적으로 묶을 순 없을까? 있다. 열거형을 이용하면 정수 상수형을 한 데로 묶을 수 있다.

#### - 열거형

> <center> enum [태그] { 리스트 }; </center>

**열거형**(enumeration)은 명명된 정수 상수의 집합으로 구성된다.  태그는 써도 되고 안써도 된다. 열거형 또한 '타입'이라는 것에 주의하자. 즉, 변수 선언이 가능하다. 열거형 변수는 열거형 집합의 값 중 하나를 지정한다.

```c++
enum Grade { Grade_F, Grade_D, Grade_C, Grade_B, GradeA };

Grade temp = Grade_F;
```
열거형은 이런 기호 상수들의 집합이기에 모든 산술 및 관계형 연산자의 피연산자로 사용할 수 있다. 또한 값이 자동으로 생성되고 어디서든 명명할 수 있는 이점을 제공한다.

열거형 집합 멤버엔 다음과 같은 규칙이 있다.
> - 중복된 상수 값이 포함될 수 있다.
> - 열거형 목록의 식별자는 표시 유형이 같은 동일한 범위에 있는 다른 식별자(다른 열거형 목록의 일반 변수 이름 및 식별자 포함)와 구별되어야 한다.
> - 첫번째 값을 지정하지 않으면, 0을 할당한다.
> - 다음 값을 지정하지 않으면 이전 값에 +1이 된 값을 할당한다.

----
## 과제

**1.** 두 정수를 입력 받아
- 앞수가 뒷수 보다 크면 >
- 앞수가 뒷수 보다 작으면 <
- 같으면 =

를 출력하는 프로그램을 작성하라.

**예시**
- 입력
```
3 4
```
- 출력
```
<
```
- 입력
```
4 4
```
- 출력
```
=
```

**2.** 컴돌이는 월,수,금 수영을 신청했다.
- 월요일
- 화요일
- 수요일
- 목요일
- 금요일
- 토요일
- 일요일

수영장을 가는 날인지 아닌지를 판별하는 프로그램을 작성하라.

**입력**
1 에서 7 사이의 자연수가 입력으로 주어진다.

**출력**
수영장 가는 날이면 enjoy , 아니면 oops 를 출력

**예시**
- 입력
```
1
```
- 출력
```
enjoy
```
- 입력
```
4
```
- 출력
```
oops
```

**3.** 자연수를 입력으로 받아 윤년이면 YES , 아니면 NO 를 출력하는 프로그램을 작성하라.
윤년이란 ,

- 4의 배수이고 100 의 배수가 아님.
- 400 의 배수임

두 가지중 하나라도 참이면 윤년

**입력**
입력되는 수는 3000 이하의 자연수이다.

**예시**
- 입력
```
4
```
- 출력
```
YES
```
- 입력
```
100
```
- 출력
```
NO
```
- 입력
```
200
```
- 출력
```
NO
```
- 입력
```
400
```
- 출력
```
YES
```

**4.** a,b,q 가 정수이고 다음 식이 만족할 때

> b = a × q (단,a‡0)

a 는 b 의 약수, b 는 a 의 배수로 약속되어 진다.
a 가 b 의 약수이면 a | b 로 표시하고 그렇지 않으면 a ł b 로 표시하는 프로그램을 작성하라.

**입력**
두 정수 m , n 이 차례로 주어진다. m , n 값으로 0 이 입력될 수 있다. (-100 <= m,n <= 100)
참고로 0 은 모든 수의 배수이고 어떤 수의 약수는 될 수 없다.

**출력**
기호 ł 는 !| 로 대신한다.
m 이 n 의 약수이면 m | n 를 아니면 m !| n 를 출력한다. 숫자와 기호 사이에는 한 칸의 공백을 둔다.

**예시**
- 입력
```
2 4
```
- 출력
```
2 | 4
```
- 입력
```
3 4
```
- 출력
```
3 !| 4
```
----
