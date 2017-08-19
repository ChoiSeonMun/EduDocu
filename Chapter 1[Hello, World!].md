<!---
ebook:
  title: Chapter 1
  author: ChoiSeonMun

  pdf:
    paper-size: letter
    default-font-size: 12
    footer-template: "<span> Written by ChoiSeonMun _PAGENUM_ </span>"
--->

### 1. Hello, World!
#### - 학습 목표
> **1.** C/C++ 발전 과정을 이해한다.
> **2.** Visual Studio 2010을 통해 디버깅, 컴파일을 할 수 있다.
> **3.** 버전 관리 시스템을 이해하고 사용할 수 있다.
> **3.** 컴파일 과정과 함수 구조를 파악한다.
> **4.** 간단한 출력을 할 수 있다.
---
#### - C/C++ 발전 과정
> - **컴퓨터**
컴퓨터(compute + er)는 본래 어원에서 알 수 있다시피 고속 계산을 위한 용도로 발전되었다. 현대 컴퓨터의 개념을 최초로 제시한 이는 찰스 배비지였는데, 그는 오늘날의 컴퓨터와 개념적으로 같은 기계인 해석기관을 설계하였다. 후에 천공카드 시스템이 개발되어 프로그래밍을 이용하게 된다.

<center>
<img src="https://goo.gl/i1Jc69" width="240" height="100">
</center>
<center>
<b>천공카드</b>        
</center>

> - **프로그래밍**
프로그래밍 언어는 컴퓨터와 의사소통할 수 있는 언어이다. 가장 원시적인 언어는 기계어이며, 이에 대응하는 어셈블리어, 그리고 고급 수준 프로그래밍 언어인 코볼, 포트란, C 등이 나왔다.

> - **C/C++**
C는 **데니스 리치**(Dennis MacAlistair Ritchie, 1941.9.9~2011.10.12)가 만든 프로그래밍 언어이다. 어셈블리어로 변환되어 속도가 매우 빠르고, 오늘날 수많은 언어들의 근간이 되는 언어이다. 메모리를 직접 제어할 수 있다는 것이 가장 큰 특징인데, 이로 인해 C언어는 고수준부터 저수준까지 접근할 수 있어 아직도 많이 쓰이는 언어 중 하나이다.
C++는 **비야네 스트롭스트룹**(Bjarne Stroustrup)이 C언어에서 파생시켜 만든 언어로서, 객체지향 프로그래밍의 개념이 추가되었다.

<center>
<img src="https://goo.gl/Hc7vVg" width="200" height="200">
</center>
<center>
<b>데니스 리치</b>        
</center>

#### - VS 2010 세팅하기
> 1. 도구->옵션->환경->글꼴 및 색에서 글꼴을 **Consolas**, 크기는 원하는 대로 바꾸어 준다.
![1](http://i.imgur.com/L2jwEEQ.png)
> 2. 텍스트 편집기->C/C++->일반에서 줄 번호를 체크한다.
![2](http://i.imgur.com/MWJm8TF.png)
> 3. 탭에서 공백 삽입으로 바꿔준다.
![3](http://i.imgur.com/W971sqI.png)
> 4. 환경->문서에서 해당 란을 체크한다.
![11](http://i.imgur.com/bkI9ybF.png)

- VS 2010에서 새 프로젝트 만들기
> 1. 파일->새로 만들기->프로젝트를 누른다.(Ctrl+Shift+N)
> 2. Visual C++에서 Win32 콘솔 응용 프로그램을 선택한다. 저장되는 위치를 바꿔도 무관하다.
![4](http://i.imgur.com/Uerbb9C.png)
> 3. 다음을 눌러 진행하고, 추가 옵션은 꼭 빈 프로젝트로 해준다.
![5](http://i.imgur.com/OmSxF5o.png)
> 4. 소스 파일에 C++ 파일을 추가한다.
![6](http://i.imgur.com/zrITNUW.png)

#### - 버전 관리 시스템(Version Control System)

버전 관리 시스템이란 파일의 변화를 시간에 따라 기록하여 과거 특정 시점의 버전을 다시 불러올 수 있는 시스템이다. 즉, 어제 했던 내용으로 돌릴 수 있는 시스템이다. 중앙 집중 시스템과 분산 버전 관리 시스템으로 나뉘며, 여러가지 종류가 있다. 우리는 그 중 Git을 이용한다. 동작 원리는 [여기](http://rogerdudler.github.io/git-guide/index.ko.html)서 참고할 수 있다.

그럼 왜 버전 관리 시스템을 사용해야 하는가? 이유는 다음과 같다.

**1.** 무언가 잘못되었을 때 복구를 돕기 위하여
**2.** 프로젝트 진행 중 과거의 어떤 시점으로 돌아갈 수 있게 하기 위하여
**3.** 여러사람이 같은 프로젝트에 참여할 경우, 각자가 수정한 부분을 팀원 전체가 동기화하는 과정을 자동화하기 위하여
**4.** 소스 코드의 변경 사항을 추적하기 위하여
**5.** 소스 코드에서 누가 수정했는지 추적하기 위하여
**6.** 대규모 수정 작업을 더욱 안전하게 진행하기 위하여
**7.** 가지내기(Branch)로 프로젝트에 영향을 최소화 하면서 새로운 부분을 개발하기 위하여
**8.** 접붙이기(Merge)로 검증이 끝난 후 새로이 개발된 부분을 본류(trunk)에 합치기 위하여
**9.** 많은 오픈 소스 프로젝트에서 어떠한 형태로든 버전 관리를 사용하고 있으므로
**10.** 코드의 특정 부분이 왜 그렇게 쓰여 졌는지 의미를 추적하기 위하여

앞으로의 모든 과제는 Git을 통해 제출한다.

- Github Desktop 설정하기
> 1. [Github Desktop 홈페이지](https://desktop.github.com/)로 들어간다.
> 2. 맨 아래에 있는 Download 버튼을 이용한다.
![3](http://i.imgur.com/MSJSc5v.png)
> 3. Github 계정으로 로그인하자.
![4](http://i.imgur.com/YJP8Z80.png)
> 4. Configure Git은 그대로 둔다. 혹여나 자기 이름으로 되어있지 않다면 수정바란다.
> 5. [여기](https://github.com/ChoiSeonMun/BasicCourse1_BCSD)에서 우측 상단의 fork를 누른다.
![6](http://i.imgur.com/M4Z8SrX.png)
> 6. 다음과 같이 Clone을 하자. 저장할 폴더는 알아서 정하도록 하자.
![7](http://i.imgur.com/TiwlD4v.png)
> 7. 해당 저장 폴더로 들어가 자기이름으로 된 폴더를 만들고, 그 폴더 안에 앞으로의 과제를 저장한다. 해당 폴더에 어떤 파일이 추가되면 다음과 같이 어플리케이션이 업데이트가 된다. Summary 부분에는 간략한 설명을 적고, Description 부분에는 상세 설명을 적는다. 그리고 Commit을 누른다.
![8](http://i.imgur.com/t5bOgmd.png)
> 8. 그리고 Pull request를 이용해 title엔 이름을 적고 Description엔 몇번째 과제인지 적는다. 그리고 send를 누른다.
![9](http://i.imgur.com/sDixsaI.png)

이러면 끝이다.

#### - Hello, World!

다음을 입력해보자. 빌드->컴파일을 누르면 컴파일을 할 수 있고, 디버그->디버깅 하지 않고 시작을 누르면 해당 프로그램의 출력화면이 뜬다.
```c++
//Hello, world 예제
#include <stdio.h>

int main(void)
{
  puts("Hello, World!");
  return 0;
}
```
<center><img src="http://i.imgur.com/5npX1XZ.png"></center>
<center> <b>실행화면</b> </center>

방금 첫 프로그래밍을 해봤다. 그럼 어떻게 실행되는 것일까? 위에서 아래로 차례대로 프로그램이 진행된다. 각 구문에 대해 좀 더 자세히 알아보자.

```c++
#include <stdio.h>
```
> #include는 **전처리기 지시어**이며, 전처리기란, 컴파일 전에 실행되는 것들을 말한다. 단어를 보면 알 수 있듯 무언가를 포함하게 하는 것인데, 헤더 파일을 포함한다. **헤더(header) 파일**은 소스 코드 파일의 일종으로 함수, 형의 선언들이 들어가 있다. <>는 라이브러리 헤더를 포함하는 것이다.

```c++
int main(void) { }
```
> main 함수이다. 프로그램이 시작될 시 이 메인 함수부터 시작하게 된다. 그럼 여기서 **함수**란 무엇일까? 함수라는 것은 일련에 과정에 이름을 붙인 것이라고 보면 된다. 함수의 구조는 다음과 같다
> <center> 반환형 함수이름(매개변수 목록) {함수 본체} </center>
> 여기서는 <code>int</code>가 반환형 <code>main</code>이 함수이름 <code>void</code>가 매개변수 목록이 될 것이다. 여기서 void는 아무것도 전달하지 않음을 뜻한다. 그리고 마침내 함수 본체가 실행이 되고 <code>int</code>형의 어떤 값을 돌려주게 된다.

```c++
puts("Hello, World!");
```
> `puts`는 라이브러리 함수이다. 함수명에 `()`연산자를 붙여주면 그 함수를 불러온다는 것이다. `puts`의 동작은 매개변수의 내용에 개행문자를 붙여 콘솔창에 출력한다.

```c++
return 0;
```
> 함수 내에서 반환할 때 `return`이라는 구문을 사용한다. 여기서는 0을 돌려주게 된다.

#### - 컴파일 과정

그럼 정확히 컴파일이 어떻게 일어나는지 알아보자. **컴파일러**(compiler)는 우리가 작성한 소스 코드를 컴퓨터가 읽을 수 있는 형태로 번역(compile)한다. 여기서는 main.cpp이 컴파일 될 것이다. 그리고, **링커**(linker)가 각 소스코드 간의 의존성을 파악하고, 결합하는 역할을 한다. 그렇게 최종적으로 실행 파일이 나오게 된다.
<center>
<img src="http://cfile21.uf.tistory.com/image/131318394D611F6612671F">
</center>

#### - 디버거(debugger)

디버깅이란, 버그를 잡는 것을 말한다. 디버거는 이러한 디버깅을 도와주는 도구이다. 대부분의 프로그래밍은 사실 디버깅에 많은 시간을 쏟게 된다. 그래서 디버거를 통해 디버깅을 하는 법을 아는 것은 매우 중요하다. 컴파일러, 링커, 디버거가 결합 된 하나의 프로그램을 **통합개발환경**(Integrated Development Environment)이라고 한다. 여기서는 VS의 기초 디버깅을 알아본다.
우선 우리의 Hello, World! 예제로 돌아가보자.
> - F9나 마우스를 통해 줄을 클릭하면 중단점을 생성할 수 있다.
![8](http://i.imgur.com/ypcMTSO.png)
> - 디버그->디버깅 시작을 누르면 중단점을 건 줄에서 프로그램이 멈추게 된다.
![9](http://i.imgur.com/sTk5U2m.png)
> - F10을 누르면 프로시저 단위로, F11을 누르면 한 단계씩 진행하게 된다.
![10](http://i.imgur.com/f5e4yQg.png)

----
## 과제

**1.** "Hello, 자기 이름"을 출력해보자.
**2.** 애국가를 출력해보자.
**3.** main 함수의 반환 값은 누가 사용하는가?
**4.** 다음 코드를 올바르게 고쳐보아라. 또한, 컴파일러의 오류 메세지도 확인해보자.
```c++
#include <stdio.h

int Main(void)
{
  puts("Hello, world)
```
**5.** 함수는 어떤 구조로 이루어져 있는가?

----
## 이미지 출처

1. 천공카드 : https://goo.gl/i1Jc69
2. 데니스 리치 : https://goo.gl/Hc7vVg
3. 컴파일 과정 : http://cfile21.uf.tistory.com/image/131318394D611F6612671F

<!---
1. 레퍼런스 사이트(MSDN, cplusplus, http://forum.falinux.com/zbxe/index.php?mid=C_LIB)
2. 주석
3. 매크로
--->
