# Pointer
* Pointer란 실행중인 프로세스의 임의의 주소를 말한다
***
# 포인터 변수
* 다른 객체의 메모리 주소를 저장하는 변수
* 포인터 변수는 실행중인 어떤 변수의 시작주소를 대입
* 형식 - 자료형 *변수이름;
* ex - int *ip;, char *ch;, double *db;
* 포인터 변수는 *, & 연사자와 함께 사용 

![image](https://user-images.githubusercontent.com/79950254/122790657-7ebaf680-d2f3-11eb-9298-2ecd8aba67cb.png)
***
# 포인터 변수 자료형과 메모리 할당
##### 1. 포인터 변수의 메모리 할당
- 선언되는 자료형과 무관 32비트 운영체제(4바이트), 64비트 운영체제(8바이트) 할당
- 즉, 어떤 자료형으로 선언된다 해도 32비트 운영체제에서는 4바이트로 할당 된다.
##### 2. 포인터 변수의 자료형
- 자신이 참조할 데이터의 자료형과 동일해야 된다
- 포인터 변수가 가리키는 번지로 가서 몇 바이트로 읽어 오는가
- 즉, 포인터 변수의 자료형 정보 크기만큼 접근
- 포인터 변수의 타입 =  포인터 변수가 접근한 데이터의 자료형
##### 3. 포인터 변수 사용 시 알아야 할 규칙
* 포인터 변수는 *변수명으로 선언
* 포인터 변수의 자료형은 자신이 참조할 변수의 자료형과 같아야함
* 포인터 변수는 실행 시 주소를 대입 받아야 함 
* 변수의 주소 "&" 연산자 사용하여 시작 주소 사용
* ***
# 포인터 사용 시 많이 틀리는 것
1. 포인터를 선언하고 주소를 대입하고 사용
2. 포인터 변수의 자료형을 자신이 참조할 변수와 같은 자료형으로 선언
3. 일반 변수는 간접참조 할 수 없다
4. 포인터 연산은 정수형 연산식을 사용
5. 포인터 변수를 초기화
***
# 다중 포인터
* 포인터 변수의 시작 주소를 다른 포인터 변수의 데이터를 이용
* 이중 포인터 변수는 선언 시 ** 하나 더 붙여 사용
