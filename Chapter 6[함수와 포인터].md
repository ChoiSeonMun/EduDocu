### 6. 함수와 포인터
#### - 학습 목표
> **1.** 함수의 동작 원리를 이해하고, 작성할 수 있다.
> **2.** 포인터의 개념을 이해한다.
> **3.** 포인터를 통해 메모리 사용을 이해한다.
> **4.** 참조자를 이해한다.
---
#### - 함수(function)

우리는 이제까지 몇 개의 함수를 사용해보았다. 첫 시간에는 시그너쳐에 대해서도 살펴보았다. 함수란 단지, 일련의 루틴에 이름을 붙여준 것에 불과하다. 라이브러리 함수 말고도 우리가 직접 함수를 작성할 수도 있다는 것을 조건문 시간에 살펴보기도 했다. 자 그럼, 못다했던 함수 얘기를 마저 마무리 지으려고 한다.

까먹은 사람들을 위해 다시 한번 함수의 구조로 돌아가보고 찬찬히 살펴보도록 하자. 우선 어떤 함수의 시그너처란 것은 반환타입과 매개변수 목록을 의미하는 것이다. 시그너처는 함수의 타입이라고도 볼 수 있다.

> <center> 반환타입 함수명(매개변수 목록) { 함수 본체 } </center>

- 반환형

해당 루틴이 끝나고 피호출자에게 돌려주는 값의 타입이다. 예를 들면, `Factorial`이라는 함수가 있다고 하자. 이 함수는 어떤 값을 인자로 받아 그 팩토리얼의 값을 반환한다. 그러니까 `2`를 주면 `2!`를 반환하게 되는 것이다. 따라서 이 함수는 적절한 반환형을 적어주어야 한다. 함수에 따라선 반환형이 없을 수도 있으며 없을 시에는 `void`를 적어주면 된다. 반환값이 있다면 `return`문을 이용해 반환할 수 있으며, 결과값은 반환형으로 변환이 될 수 있어야한다.

- 함수명

함수이름이다. 식별자 명명 규칙을 따른다. 시그너쳐만 다르다면<small>(반환형 제외)</small> 같은 이름으로 쓸 수 있다.

```c++
void Foo();
void Foo(int); //ok
void Foo(int, int); //ok
void Foo(double); //ok
int Foo(); //wrong.
```

이를 **오버로딩**(overloading)이라고 한다.

- 매개변수(parameter) 목록

매개변수라는 것은 그 함수 내에서 쓰이는 변수를 말한다. `Factorial`함수에서는 정수 값 하나를 받는다고 하였다. 따라서 `int Factorial(int num)`이 될 것이다. 매개변수를 초기화 시켜주는 값을 **인자**(argument)라 한다. 함수의 기본 동작은 '복사'이기 때문에 매개변수가 변화했다고 인자가 변하는 것은 아니다. 이를 일컬어 'call by value' 혹은 'pass by value'라고 한다.

- 함수 본체

함수가 실행되는 본문이다.

구구단을 출력하는 함수를 실제 작성해 가면서 함수 작성을 이해해보자. 아래 예제는 1단부터 9단까지 출력하는 프로그램이다.

```c++
//함수 예제 - 1
#include <stdio.h>

int main()
{
  for (int i = 1; i <= 9; ++i)
  {
    printf("%d단\n", i);
    for (int j = 1; j <= 9; ++j)
    {
      printf("%d x %d = %d\n", i, j, i * j);
    }
    puts("-------------------");
  }

  return 0;
}
```

만일 사용자로부터 입력을 받아 특정 단만 출력하려고 하면 어떻게 해야 할까? 이렇게 적을 수 있을 것이다.

```c++
//함수 예제 - 2
#include <stdio.h>

int main()
{
  puts("출력하고자 하는 단수를 입력하세요.");
  int num;
  scanf("%d", &num);
  printf("%d단\n", num);
    for (int j = 1; j <= 9; ++j)
    {
      printf("%d x %d = %d\n", num, j, num * j);
    }
    puts("-------------------");
  }

  return 0;
}
```

이 과정에 이름을 붙여 가독성을 높이고, 유지보수를 쉽게 하려고 한다. 함수명은 `PrintGugu`로 한다. 딱히 돌려줄 반환값이 없기 때문에 반환 타입은 `void`로 하고, 매개변수로는 정수값 하나를 받는다. 이렇게 해서 만든 함수는 다음과 같을 것이다.

```c++
//함수 예제 - 3
void PrintGugu(int num)
{
  printf("%d단\n", num);
    for (int j = 1; j <= 9; ++j)
    {
      printf("%d x %d = %d\n", num, j, num * j);
    }
    puts("-------------------");
  }
}
```

호출 방법은 다음과 같다.

```c++
//함수 예제 - 4
#include <stdio.h>

int main()
{
  puts("출력하고자 하는 단수를 입력하세요.");
  int num;
  scanf("%d", &num);
  PrintGugu(num);

  return 0;
}
```

함수 호출시 유의해야 할 것은 호출 전 정의를 해놓거나, 전방 선언 후 정의를 따로 구현해야 한다는 것이다.

#### - 포인터(pointer)

- 선언 및 정의

영어단어 'point'에는 '~를 가리키다'라는 뜻이 있다. 'pointer'라는 이름은 거기에 접두사 'er'이 붙은 것 밖에 없다. 즉, 무언가를 가리키는 녀석이라는 것이다. 포인터 변수는 주소값을 담는 변수인데, 이 주소를 가지고 간접적으로 접근할 수 있기 때문에 이러한 이름이 붙은 것이다. 선언 방법을 보자.

> <center> 타입 * 식별자 <center>

이 뜻은 해당 타입 객체의 '주소를 담는 포인터 변수라는 뜻이다.선언하는 스타일은 사람마다 다른데 다음과 같이 세 가지가 있다. `int *ptr`, `int* ptr`, `int * ptr`. 여기서는 두 번째 형식을 쓰도록 하겠다.

포인터 변수의 크기는 운영체제에 따라 다르다. 32비트 운영체제에서는 4바이트 만큼의, 64비트 운영체제에서는 8바이트 만큼의 크기를 갖는다.

포인터는 메모리와 직접적으로 상호작용하기 때문에 다양한 일을 할 수 있게 된다. 하지만, 그만큼 쓰는데 충분한 주의가 필요하다. 그렇지 않으면 프로그램이 망가지게 된다.

<p>
<center>
<img src="http://cfs10.tistory.com/original/16/tistory/2009/06/24/15/07/4a41c2a267496">
</center>
<center> <b>이런게 다 포인터 오류로 인해서 생기는 것이다.</b> </center> </p>

- 간접참조 연산자

 `*` 연산자는 간접참조(indirection or dereferencing) 연산자라고 한다. 이 연산자로 포인터에 담겨진 객체의 내용을 변경할 수 있다.

 ```c++
 // 포인터 예제 - 1
 int a = 10;
 int* pti = &a; // pti : pointer to int
                // &연산자로 객체의 주소값을 준다는 것을 인지하자
 *pti = 20;     // a의 값은 20으로 변하게 된다.
 ```

 포인터 변수의 타입은 가리키는 타입과 반드시 일치해야 한다.


 - 초기화

 포인터 변수의 초기화는 어떤 변수의 주소값으로 초기화한다. 아무것도 가리키지 않을 때에는 `0`, `NULL`, `nullptr`을 이용해 초기화하면 된다. 아무것도 가리키지 않는 포인터를 간접참조하면 런타임 에러가 발생한다.

 - 주소 연산

 포인터에 적용할 수 있는 연산은 `+, -, 증감연산자`이다. 피연산자로는 정수 값을 받는다. 이 연산들은 해당 포인터들을 이동시킨다.

 <center>
 <img src="data:image/png;base64,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" width = 400>
 </center>

- 함수와의 관계

포인터는 간접 참조할 수 있다는 특징 때문에 함수 내에서 원본을 조작할 때 이용되기도 한다. 예를 들어, 두 정수를 바꾸는 `swap`이라는 함수가 있다고 해보자.

```c++
//포인터 예제 - 2
#include <stdio.h>

void swap(int lval, int rval) // 틀림
{
  int temp = lval;
  lval = rval;
  rval = temp; // 원본과 매개변수는 다른 값이다.
}

int main()
{
  int val1 = 10;
  int val2 = 20;
  printf("swap()호출 전 값 : %d, %d\n", val1, val2); //10 20
  swap(val1, val2);
  printf("swap()호출 후 값 : %d, %d\n", val1, val2); //10 20
                                                    //변함이 없다.
  return 0;
}
```

원래 함수의 '값으로 전달'방식으로는 도저히 구현할 수가 없다. 하지만 매개변수에 포인터를 쓰면 가능하다.

```c++
//포인터 예제 - 3
#include <stdio.h>

void swap(int* lval, int* rval)
{
  int temp = *lval;
  *lval = *rval;
  *rval = temp;
}

int main()
{
  int val1 = 10;
  int val2 = 20;
  printf("swap()호출 전 값 : %d, %d\n", val1, val2); //10 20
  swap(&val1, &val2); //주소값을 넘겨준다!
  printf("swap()호출 후 값 : %d, %d\n", val1, val2); //20 10

  return 0;
}
```

주소값을 전달한다는 점을 명심하자.

이러한 특성을 이용해 여러 개의 반환값을 돌려주는 것도 가능하다. `int foo(int, int*)`와 같은 함수로 보자면, `foo()`의 반환값과 두번째 매개변수 `int*`을 이용해 두개의 반환값을 돌려주게 되는 것이다.

- 상수성

변수에 `const` 기호를 붙이면 상수성을 부여할 수 있다는 것을 기억하는가? 포인터도 마찬가진데, 포인터는 두 부분에 상수성을 줄 수 있다.

> - 상위 const
>
> 가리키는 '주소값'에 상수성을 부여하는 것이다. 즉, 여기에 상수성을 부여시키면 연산이 불가능하다. 한번 가리킨 대상은 변수가 소멸될 때까지 그 곳만 가리키게 된다. 선언 방식은 `type* const`이다. 간접참조 연산자 뒤에 `const`를 붙이다는 것에 유의하자.
> - 하위 const
>
> 가리키는 '타입'이 상수임을 알리는 것이다. 주소 연산은 가능하다. 선언 방식은 `const type*` 혹은 `type const*`이다.

당연히 상위 하위 둘 다에 상수성을 부여할 수 있다.

- 함수 포인터

함수를 가리키는 포인터도 선언할 수 있다. 함수의 시그너쳐를 이용하면 된다. 가령 `void foo(int, int)`라는 함수를 가리키는 포인터는 `void (*fptr)(int, int)`이다. 눈치 챈 사람도 있겠지만, 함수 선언에서 이름 대신 포인터 선언으로 바뀐 것 밖에 없다.

#### - 참조자

- 선언 및 정의

**참조자**(reference)는 상수 포인터라고 볼 수 있다. 초기화가 필요하고, 초기화를 하면 일반 변수 쓰듯 자유롭게 쓸 수 있다. 선언 및 정의 방법은 다음과 같다.

> <center> 타입 & 식별자 </center>

앞의 `swap()`을 참조자를 이용해 동일한 기능을 하지만 다른 모양을 지닌 녀석으로 바꿔보겠다.

```c++
//참조자 예제 - 1
#include <stdio.h>

void swap(int& lval, int& rval)
{
  int temp = lval;
  lval = rval;
  rval = temp;
}

int main()
{
  int val1 = 10;
  int val2 = 20;
  printf("swap()호출 전 값 : %d, %d\n", val1, val2); //10 20
  swap(val1, val2); //주소값을 넘겨주지 않아도 된다!
  printf("swap()호출 후 값 : %d, %d\n", val1, val2); //20 10

  return 0;
}
```

일단 보다시피 간접참조 연산자가 사라졌다. 또한, 호출할 때도 주소 연산자를 쓸 필요가 없다. 하지만 참조자는 내장 타입을 위해서라기 보다 나중에 배울 클래스를 위해 고안된 것이라는 것을 알아두길 바란다.

----
## 과제

**1.** 매개변수와 인자의 차이점은 무엇인가?

**2.** 저번 시간에 과제로 풀었던 문제들을 함수로 풀어보라.

**3.** 다음 함수의 잘못된 점이 있다면 고치고, 왜 그렇게 고쳤는지 이유를 설명하라.
```c++
int* foo(void)
{
  int temp = 20;
  return &temp;
}
```

**4.** 상위 const와 하위 const가 무엇인지 설명하라.

**5.** 함수 시그너쳐가 `int(double, char)`일 때, 이 함수를 가리키는 포인터를 정의해보자.

----
## 이미지 출처
1. 메모리 이미지 : http://befreepark.tistory.com/623
2. 주소 연산 : https://dojang.io/mod/page/view.php?id=509
