## Issue
goto문 사용시 error: jump to label, crosses initialization of Error 발생.

## Cause
- goto문 코드 아래의 같은 영역에 변수 선언이 있는 경우, 컴파일러에 따라 Error 가 발생하는 경우가 있음.

## Solution
- goto문 아래의 변수 선언 부를 별도의 영역으로 처리하여 해결 가능함.
   + 단순히 { } 중괄호를 이용한 영역 구분으로도 해결 가능함.
- 예시

   |Error 발생|수정함|
   |:---:|:---:|
   |![image](https://user-images.githubusercontent.com/26864945/69923738-87b65e00-14ea-11ea-8bc7-9bda016a8780.png)|![image](https://user-images.githubusercontent.com/26864945/69923766-b0d6ee80-14ea-11ea-8658-95ef3ec5bddf.png)|
   |![image](https://user-images.githubusercontent.com/26864945/69923799-ce0bbd00-14ea-11ea-98db-c2c816530462.png)|![image](https://user-images.githubusercontent.com/26864945/69923831-f1366c80-14ea-11ea-9352-00b0f334e79a.png)|

