# Issue
C/C++ 파일 간 함수 호출 시 undefined reference to Error 발생.

## Cause
- C++ toolchan 은 C 파일과 CPP 파일 컴파일을 모두 지원함.
- C 파일은 C 언어로 컴파일 됨.
- CPP 파일은 C++ 언어로 컴파일 됨.
- C 파일에서는 클래스 정의 불가.
- **`같은 이름의 함수라도 C/C++ 에 따라 어셈블러에서 다르게 변환됨.`**
   > _위의 이유로 C 코드내에서 CPP 코드에 작성한 함수에 접근시 아래 처리를 하지 않으면 undefined reference to Error 발생함._
- 예시

   |wmfwparse.h|wmfwparse.cpp|passthru.c|
   |:---:|:---:|:---:|
   |![image](https://user-images.githubusercontent.com/26864945/69854582-c66ecd00-12cc-11ea-950f-13e7cde8a17a.png)|![image](https://user-images.githubusercontent.com/26864945/69854630-e605f580-12cc-11ea-8fc3-0b19cccee59f.png)|![image](https://user-images.githubusercontent.com/26864945/69854715-1e0d3880-12cd-11ea-96ab-74f5be5141d9.png)|

   ![image](https://user-images.githubusercontent.com/26864945/69854940-b7d4e580-12cd-11ea-96f4-b471ac556aaa.png)

## Solution
- **C++ 에서 제공하는 `extern "C"` 사용함.**
   ```c
   #ifdef __cplusplus
   extern "C" {
   #endif
   int ProcessWMFWFile(const char *filename);
   #ifdef __cplusplus
   }
   #endif
   ```
- 예시

   |wmfwparse.h|wmfwparse.cpp|passthru.c|
   |:---:|:---:|:---:|
   |![image](https://user-images.githubusercontent.com/26864945/69855149-32056a00-12ce-11ea-94d8-a816ea16bd1f.png)|![image](https://user-images.githubusercontent.com/26864945/69854630-e605f580-12cc-11ea-8fc3-0b19cccee59f.png)|![image](https://user-images.githubusercontent.com/26864945/69854715-1e0d3880-12cd-11ea-96ab-74f5be5141d9.png)|
