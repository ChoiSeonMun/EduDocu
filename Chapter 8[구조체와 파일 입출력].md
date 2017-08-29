### 8. 구조체와 파일 입출력
#### - 학습 목표
> **1.** 구조체를 사용할 수 있다.
> **2.** 파일 입출력을 사용할 수 있다.
---
#### - 구조체

- 선언 및 정의

저번 시간에는 같은 자료형의 묶음인 배열에 대해서 배워보았다. 이번 시간에는 다양한 자료형을 한 데 묶을 수 있는 구조체에 대하여 살펴보겠다. 구조체는 다음과 같이 선언 및 정의한다.

> <center> struct 구조체-태그 { 여러 자료형 }; </center>

구조체 정의는 보통 헤더파일에 적는다. 예시로, 학생이라는 구조체를 한번 만들어보도록 하겠다. 학생에는 이름, 학번, 전공, 나이 등이 있을 것이다.

```c++
struct Student
{
  char name[NAME_SIZE];
  char ID[ID_SIZE];
  char major[MAJOR_SIZE];
  unsigned age;
};
```

구조체를 실제로 사용하려면 구조체 변수를 정의해야 한다.

```c++
struct Student a; // struct 키워드 생략 가능
```

C에서는 `struct` 키워드를 써야 했지만, C++에서는 생략해도 무방하다. 앞으로는 생략하도록 하겠다.

- 초기화

초기화는 `{}` 연산자를 이용하여 초기화 할 수 있다.

```c++
Student csm = { "ChoiSeonMun", "2014136127", "Computer Engineering", 23 };
```

- 접근

각 데이터는 `.` 연산자를 이용해서 접근할 수 있다. 예를 들어 `csm`이 개명이 되었다고 한다면 이런식으로 할 수 있을 것이다.

```c++
strcpy(csm.name, "ChoiSeonJoong");
```

덧붙여, `->`연산자도 함께 보면 좋은데, 이는 포인터에서 이용되는 방식이다. 다음을 보자.

```c++
Student* a = (Student*)malloc(sizeof(Student));
strcpy(a->name, "ChoiSeonMun"); // a->name은 (*a).name과 동일
strcpy(a->ID, "2014136127"); // a->ID는 (*a).ID와 동일
strcpy(a->major, "Computer Engineering"); // a->major는 (*a).major와 동일
a->age = 23; // a->age는 (*a).age와 동일
free(a);
a = nullptr; // NULL or 0
```

#### - 파일 입출력

파일 입출력이란 파일로부터 입력을 받거나, 파일로 출력을 하는 것을 의미한다. 사실 이제까지도 여러분들은 인지하지 못했겠지만 파일 입출력을 하고 있었다. 콘솔 창으로 입출력을 했던것은 `stdin`, `stdout`으로 입출력을 하는 것과 마찬가지이다. 파일 입출력과 관련된 함수는 무엇이 있고, 어떻게 사용하는 것인지 알아보자.

- 파일 포인터

파일을 사용하려면 `<stdio.h>`에 있는 `FILE` 구조체에 대한 포인터를 사용해야한다. 그리고 `fopen()`을 이용해 파일에 대한 포인터를 얻고 읽기나 쓰기 모드를 지정해줘서 사용하면 된다.

```c++
#include <stdio.h>

int main()
{
  FILE* fp = fopen("Hello, File.txt", "w");
  fputs("Hello, File!", fp);
  fclose(fp);
  return 0;
}

```

한 구문씩 살펴보자.

```c++
FILE* fp = fopen("Hello, File.txt", "w");
```

파일 포인터를 정의하고 `fopen()`함수를 이용해 바로 초기화를 했다. `fopen()`에는 두 개의 매개변수가 들어가는데, 하나는 파일 이름이고, 다른 하나는 모드이다. 모드는 다음과 같은 것들이 있다.

| 파일 모드  | 설명 |
| :------------ | :----------- |
| "r" | 파일을 읽기 전용으로 연다. 단, 파일이 반드시 있어야 한다. |
| "w" | 새 파일을 생성한다. 만약 파일이 있으면 내용을 덮어쓴다. |
| "a" | 파일을 열어 파일 끝에 값을 이어 쓴다. 만약 파일이 없으면 파일을 생성한다. |
| "r+" | 파일을 읽기/쓰기용으로 연다. 단, 파일이 반드시 있어야 하며 파일이 없으면 NULL을 반환한다. |
| "w+" | 파일을 읽기/쓰기용으로 연다. 파일이 없으면 파일을 생성하고, 파일이 있으면 내용을 덮어쓴다. |
| "a+" | 파일을 열어 파일 끝에 값을 이어 쓴다. 만약 파일이 없으면 파일을 생성한다. 읽기는 파일의 모든 구간에서 가능하지만, 쓰기는 파일의 끝에서만 가능하다. |
| t | 파일을 읽거나 쓸 때 개행문자 \n와 \r\n을 서로 변환한다. ^Z 파일의 끝으로 인식하므로 ^Z까지만 파일을 읽는다. |
| b | 파일의 내용을 그대로 읽고, 값을 그대로 쓴다. |

`t`나 `b`는 추가적으로 입력해주는 부분이며, 단독적으로 쓰이지 못한다. 그럼 우리가 쓰기 모드로 열었다는 것을 알 수 있을 것이다. 우리가 불러온 파일은 존재하지 않으므로 새로 생성될 것이다.

```c++
fputs("Hello, File!", fp);
```

입출력 함수중 하나이다. 어디선가 많이 본듯하다. 맞다. `puts()`와 비슷하다. 다만, 매개변수가 하나 더 붙어있고, 이 함수는 뒤에 개행 문자를 붙이지 않는다는 점이 틀리다. 뒤의 매개변수는 파일 포인터를 넣어준다.

```c++
fclose(fp);
```

`fclose()`는 열려 있는 파일을 닫아주는 함수이다. 파일을 닫아주지 않으면 파일에 손상이 일어날 수도 있다. 우리가 메모리 할당을 하면 해제를 하듯이, 꼭 닫아주는 습관을 가지도록 하자.

- 파일 관련 함수

여러가지 함수들이 있지만, 그 중 몇 가지만 살펴본다. 이외의 함수들은 필요하면 직접 레퍼런스 사이트에서 찾아보길 바란다.

> - fprintf : 서식에 맞춰 파일에 출력하는 함수
`int fprintf ( FILE * stream, const char * format, ... )`
> - fscanf : 서식에 맞춰 파일로부터 입력 받는 함수.
`int fscanf ( FILE * stream, const char * format, ... )`
> - fread : 파일로부터 데이터 블록을 읽는다.
`size_t fread ( void * ptr, size_t size, size_t count, FILE * stream );`
> - fwrite : 파일로 데이터 블록을 쓴다.
`size_t fwrite ( const void * ptr, size_t size, size_t count, FILE * stream );`
> - fseek : 파일 포인터의 위치를 재배치한다.
`int fseek ( FILE * stream, long int offset, int origin )`
> - ftell : 현재 파일 포인터의 위치를 구한다.
`long int ftell ( FILE * stream )`
<!--- 구두로 설명 --->

----
## 과제

**1.** 텍스트 모드와 바이너리 모드의 차이점은 무엇인가?

**2.** 다음 소스 코드를 완성하여 문자열을 hello.txt 파일로 저장하라.

```c++
#include <stdio.h>
#include <string.h>

int main()
{
    char s1[20] = "안녕하세요.";

    FILE *fp = ①______________________________

    ②______________________________

    fclose(fp);

    return 0;
}
```

**3.** 파일의 크기를 구하는 함수 `int GetFileSize(FILE* fp)`을 구현해보라.

**4.** 문자열이 저장된 words.txt 파일이 주어질 때, 파일 처음부터 순방향으로 7바이트 지점에서 4바이트만큼 읽고, 파일 끝에서 역방향으로 6바이트 지점에서 2바이트만큼 읽은 값을 출력하는 프로그램을 작성하라. 단, 읽은 문자열은 공백으로 띄우지 않고 붙여서 출력한다.
**예시**
- words.txt
```
Hello, world!
```
- 실행 결과
```
worlwo
```

**5.** choiseonmun.bin 파일로부터 `Student` 구조체를 불러들여 `stdout`으로 출력해보라.

**예시**
- choiseonmun.bin
```
choiseonmun
2014136127
Computer Engineering
23
```

- 실행 결과
```
choiseonmun
2014136127
Computer Engineering
23
```
----
