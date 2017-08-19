<!---
ebook:
  title: Chapter 5
  author: ChoiSeonMun

  pdf:
    paper-size: letter
    default-font-size: 12
    footer-template: "<span> Written by ChoiSeonMun _PAGENUM_ </span>"
--->

### 5. 반복문
#### - 학습 목표
> **1.** for, while, do while문에 익숙해진다.
> **2.** break, continue, goto문으로 반복문을 제어해본다.
> **3.** 무작위 값을 만들어 낼 수 있다.
---
#### - 반복문(loop statement)

우선, 들어가기 전, 다음과 같이 출력하는 프로그램을 작성해보자.

<center>
<img src="http://i.imgur.com/pozgfW5.png">
</center>

아마도 여러분은 이런 식으로 짰을 것이다.
```c++
#include <stdio.h>

int main()
{
  puts("*");
  puts("**");
  puts("***");
  puts("****");
  puts("*****");
  puts("******");
  puts("*******");
  puts("********");
  puts("*********");
  puts("**********");
  return 0;
}
```

그럼, 20개를 작성해보라면 어떤 기분이겠는가? 100개는? 1000개는? 사람은 단순하고 반복적인걸 귀찮아 할 뿐더러 실수의 여지가 있다. 반면에, 컴퓨터는 반복적인 일을 실수 없이 아주 빠르게 잘 해낸다. 이번에는 우리의 귀찮음을 줄여 줄 반복문을 배우게 된다. 반복문엔 세 가지가 존재한다. `for`, `while`, `do while`. 하나씩 살펴보자.

- `for`
<blockquote>
  <center>
  for (초기문; 조건문; 루프문) 구문;
  </center>
</blockquote>

`for`은 보통 몇 번동안 반복되는지에 주로 쓰인다. 초기문은 단 한번만 실행되며, 이 구문엔 보통 루프 변수를 초기화한다. 조건문은 해당 조건문이 참이면 계속 실행하고 거짓이면 멈추게 된다. 루프문은 루프 변수를 조작하는 내용이 들어있다.

순서는 다음과 같다.

<center>
<img src="http://cfile9.uf.tistory.com/image/241A385055D53C6D1D5E06">
</center>

그럼 한줄에 별 100개를 출력하는 프로그램을 작성해보자.

```c++
//for문 예제 - 1
#include <stdio.h>

int main()
{
  for (int i = 0; i < 100; i += 1)
  {
    printf("*");
  }
  // 또는 이렇게 쓸 수 있다.
  /*for (int i = 1; i <= 100; i += 1)
  {
    printf("*");
  }*/
}
```

반복 횟수를 결정할 때, 저렇게 두 가지로 나눌 수 있다. 잘 알아두자. 여기서 새로운 산술 연산자를 하나 익혀둘 필요가 있다. 바로 전위 증감 연산자이다.
> <center> ++i </center>
> <center> --i </center>

이것은 `i += 1`, `i -= 1`와 의미적으로 다를 바가 없다. 전위 증감 연산자를 쓰면 좀 더 명확하게 의미가 다가온다. 그럼 한번 바꿔보자.

```c++
//for문 예제 - 2
#include <stdio.h>

int main()
{
  for (int i = 0; i < 100; ++i)
  {
    printf("*");
  }
  // 또는 이렇게 쓸 수 있다.
  /*for (int i = 1; i <= 100; ++i)
  {
    printf("*");
  }*/
}
```

아까와 전혀 다를 것이 없다.

- 중첩 반복문

자 그럼 처음에 했던 것처럼 별을 출력하려면 어떻게 해야할까? 일단 한번 분석해보자. 줄 수를 1부터 시작한다고 할 때, 각 줄에는 줄 수만큼 별이 출력되고, 개행된다. 그것이 총 10번 반복되는 구조이다. 반복문의 구조가 보이는가? 밑의 코드를 보지 말고 작성해보자.

```c++
//for문 예제 - 3
#include <stdio.h>

int main()
{
  for (int i = 1; i <= 10; ++i)
  {
    for (int j = 0; j < i; ++j)
    {
      printf("*");
    }
    puts("");
  }

  return 0;
}
```

이런식으로 구문엔 반복문을 또 집어넣어, 이중, 삼중, 사중 등등 중첩 반복문을 만들 수 있다. 하지만 너무 중첩시킬 경우, 가독성과 성능이 떨어질 수 있다. 루프를 줄일 수 있다면 최대한 줄이고, 줄일 수 없을 경우 함수를 적절하게 이용해보자.

- `while`
> <center> while (조건) 구문; </center>

조건이 참'일 동안' 구문을 실행한다. 조건이 거짓이 되면 반복문이 끝난다. 작동 방식은 다음과 같다.
<center>
<img src="http://cfile29.uf.tistory.com/image/23451C4955D552CE153D8D">
</center>
보통 반복 횟수가 정해져 있지 않거나, 무한 루프 등에 사용한다. 일단, for문 첫번째 예제인 별 100개를 출력하는 프로그램을 `while`을 사용해 작성해보자.

```c++
//while 예제 - 1
#include <stdio.h>

int main()
{
  int i = 0; // while은 초기문이 없다.
  while (i < 100)
  {
    printf("*");
    ++i // 중요. while은 루프문이 없다.
  }

  return 0;
}
```

`while`문은 `for`문과 다르게 초기문과 루프문이 없다는 것을 인지해두자.

`while`문은 반복 횟수가 일정하게 정해지지 않을 때, 주로 쓰인다는 말 기억하는가? 이번에는 무작위로 별을 출력하게 해보자.

```c++
//while 예제 - 2
#include <stdio.h>
#include <stdlib.h> //rand()를 위함

int main()
{
  int i = 0;
  int end = rand() % 100 + 1; // 1 ~ 100까지의 수 중 임의의 수로 초기화한다.
  while (i < end)
  {
    printf("*");
    ++i
  }

  return 0;
}
```

한번 실행해보자. 어떤가? 무작위로 실행이 되는가? 일단, 첫번째 예제와 비교해봤을 때, 뭔가 길이가 달라진 것 같다. 한번 다시 실행해보자. 어떤가? 달라졌는가? 별이 너무 많아 구분이 힘들다면 적절히 조건문을 넣어 10개씩 끊어 확인해보자. 그럼 달라지지 않았다는 것을 확인할 수 있다.

왜냐하면, `rand()`의 함수 작동 방식이 시드 값에 따라 달라지기 때문이다. `rand()`는 어떤 수를 그냥 나열해놓고 호출될 때마다 하나씩 하나씩 반환시킨다. 따라서 `srand()`를 이용해 시드 값을 바꿔줘야 한다. 시드 값은 보통 시스템 시간을 사용한다.

```c++
//while 예제 - 3
#include <stdio.h>
#include <stdlib.h> //srand(), rand()
#include <time.h> //time()

int main()
{
  int i = 0;
  srand(time(0)); //현재 시간으로 시드 값을 준다.
  int end = rand() % 100; // 0 ~ 99까지의 수 중 임의의 수로 초기화한다.
  while (i < end)
  {
    printf("*");
    ++i
  }

  return 0;
}
```

이제는 실행할 때마다 계속 다른 결과가 나올 것이다.

- `do while`
> <center> do {구문;} while(조건); </center>

뒤의 세미콜론을 빼먹지 않도록 주의하자. 작동 방식은 다음과 같다.
<center>
<img src="http://cfile27.uf.tistory.com/image/2175744355D55C6D0DA0C7">
</center>

앞의 `while`과 다르게 `do while`은 무조건 한 번은 작동하게 되어 있다는 걸 인지해두자. 다음과 같은 메뉴 출력에 이용해볼 수 있을 것이다.

```c++
//do while 예제 - 1
#include <stdio.h>

void PrintMenu();
enum Menu { START_GAME = 1, CREATE_MAP, QUIT };

int main()
{
  int input = 0;
  do {
    PrintMenu();
    scanf("%d", &input);
  } while (input < START_GAME && input > QUIT);

  switch (input) {
    case START_GAME: StartGame(); break;
    case CREATE_MAP: CreateMap(); break;
    default:                      break;
  }

  return 0;
}

void PrintMenu()
{
  puts("1. 게임 시작");
  puts("2. 맵 만들기");
  puts("3. 종료");
}
```

배달맨 코드를 일부 사용한 것이다. 사용자로부터 입력을 받기 전에 일단 먼저 메뉴창을 출력해야 할 것이다. 입력을 받고 그 입력이 올바른 것인지 판단한다. 올바른 입력이 아니면 다시 메뉴를 출력해야 할 것이다. 이런 구조엔 `do while`이 제격이다.

또한, 함수 매크로를 작성하는 데에도 쓰인다. 여기서는 자세히 알아보진 않는다.

- 제어하기

반복을 하다가도 특정 조건이 되면 나가거나, 실행하지 않는 동작이 필요할 때가 있다. 이런 제어를 하기 위한 구문들도 존재한다. `break`를 이용하면 반복문을 탈출할 수 있고, `continue`를 이용하면, 다음 루프로 넘어갈 수 있으며, `goto`를 이용하면 원하는 곳으로 코드 진행을 옮길 수 있다. 예제를 통해 하나하나 살펴보자.

- `break`

이미 `switch`문에서 사용해봤다. 반복문에서도 이 구문을 만나면 멈춘다.

```c++
//제어 예제 - 1
for (int i = 0; i < 100; ++i)
{
  if (i == 10)  //i가 10이 되면
    break;      //멈춘다.
}
```

이 예제에서의 `for`문은 본디 100번을 반복하도록 되어 있으나, `break`문을 이용해 10번만 반복하도록 해놓았다는 걸 볼 수 있을 것이다.

- `continue`

`continue`문은 동작을 정지하는 것이 아니라, 다음 루프로 이동한다. `for`문에서는 루프문으로 이동하며, `while`, `do while`에서는 조건문으로 이동한다.

```c++
//제어 예제 - 2
for (int i = 0; i < 100; ++i)
{
  if (i % 2)
    continue;
  printf("%d", i);
}
```

이 예제에서는 짝수만 출력하게끔 되어 있다. 홀수면 `continue` 아래에 있는 구문을 실행하지 않고 루프문으로 이동한다.

다음의 예제를 보자.

```c++
//제어 예제 - 3
#include <stdio.h>

int main()
{
  int num1 = 0;
  int num2 = 0;
  for (int i = 0; i < 100; ++i)
  {
    for (int j = 0; j < 100; ++j)
    {
      ++num2;
    }
    ++num1;
  }

  return 0;
}
```

이 예제는 첫번째 `for`문에서는 `num1`을 1씩 증가시키고, 두번째 `for`문에서는 `num2`를 1씩 증가시킨다. 자 그럼 여기서 `num2`가 30이 되었을 때, 모든 반복문을 중지하고 나오도록 프로그램을 작성해보자.

원하는 바대로 되었는가? `printf()`를 이용해 각 값들을 출력해서 확인해보자. 아마 잘 안되었을 것이다. 왜냐하면 `break`문은 단 하나의 반복문만 끝내기 때문이다. 이런 중첩 반복문에서 나갈려면 `goto`를 사용해야 한다.

- `goto`
> <center> goto 레이블; </center>

아까의 예제를 다시 작성해보자.
```c++
//제어 예제 - 4
#include <stdio.h>

int main()
{
  int num1 = 0;
  int num2 = 0;
  for (int i = 0; i < 100; ++i)
  {
    for (int j = 0; j < 100; ++j)
    {
      if (num2 == 20)
        goto EXIT;
      ++num2;
    }
    ++num1;
  }
EXIT:     //레이블
  printf("num1 : %d, num2 : %d\n", num1, num2);
  return 0;
}
```
이제는 잘 작동한다.

하지만, `goto`를 쓸 땐 주의할 점이 있다. 코드 흐름을 절대 앞쪽으로 위치시켜서는 안되며, 중첩 반복시에만 사용해야 한다. `goto`문을 남발하게 되면 코드의 이해도 어려워지고, 흔히 '스파게티 코드'가 만들어진다. 중첩 반복문을 벗어나는 것이 아니라면 `goto`문을 쓰지 말자.

----
## 과제

**1.** 각 반복문 별로 무한반복을 하는 코드를 작성해보자.

**2.** 사용자로부터 특정 수를 입력 받아, 그 수만큼 별을 출력해보자.

**예시**
- 입력
```
10
```
- 출력
```
**********
```

**3.** FizzBuzz 프로그램을 작성해보라. FizzBuzz는 2의 배수일땐 Fizz를 출력하고, 5의 배수일땐 Buzz를 출력한다. 2와 5의 공배수라면 FizzBuzz를 출력한다. 반복횟수는 100으로 한다.

**예시**
- 출력
```
1
Fizz
3
4
Buzz
Fizz
7
Fizz
9
FizzBuzz
11
Fizz
... //후략
```

**4.** 7개의 수열 중에서 최소 값과 최대 값을 출력하는 프로그램을 작성해보라.

**예시**
- 입력
```
6 2 9 8 3 4 7
```
- 출력
```
9 2
```

**5.** 자연수가 입력으로 주어질 때, 이 수의 약수를 출력하고 , 다음 줄에는 약수의 개수 , 다음 줄에는 약수의 총합 , 다음 줄에는 약수의 곱의 일의 자리수를 출력하는 프로그램을 작성해보자. 입력은 1000 이하의 자연수로 한정한다.

**예시**
- 입력
```
6
```
- 출력
```
1 2 3 6
4
12
6
```

----
