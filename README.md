
> 스택 활용 - 계산기 프로그램 구현

  1단계) 중위 -> 후위 변환 프로그램 구현 
    - InfixToPostfix.h // ConvToRPNExp 함수 선언
    - InfixToPostfix.c // ConvToRPNExp 함수 정의
    - ListBaseStack.h // 스택 활용
    - ListBaseStack.c


  2-1단계) 후위 표기법 수식의 계산방법
       ex) 3 2 4 * +
         - 먼저 연산 되어야 하는 연산자가 수식들 앞쪽에 위치함.
           - 따라서, * -> +
         - 후위 표기법의 수식에서는 연산자의 앞에 등장하는 두 개의 숫자가 피연산자임.
           - 3 "2 4 *" +
           - "3 8 +"
           - 11

       ex) 1 2 * 3 + 4 /
         - 수식 젤 앞이 * 이므로, * 부터 연산한다.
         - "1 2 *" 3 + 4 /
         - 2 3 + 4 /
         - 5 4 /
         - 1.25 // double형 변수, if 정수형 -> 1


ex3) 다음 후위 표기법의 수식을 계산
     1) 4 2 * 8 +
     2) 1 2 3 + * 4 /


  2-2단계) 후위 표기법 수식의 계산구현
    1) 피연산자(숫자)는 무조건 스택으로 옮긴다.
    2) 연산자 만나면, 스택에서 두 개의 숫자 꺼내서 계산한다.
    3) 계산 결과를 다시 스택에 넣는다.

    ex) [3][2][4][*][+]

      1) [ ][ ][ ][*][+]
         [3][2][4] (스택)

         - 3,2,4 모두 피연산자이니, 스택에 Push

      2) [ ][ ][ ][ ][+]
         [3][8] (스택)

         - 이제 *를 처리할 차례.
         - 스택에서 두 개의 숫자 꺼내서 연산 진행 후에, 다시 스택에 집어 넣기.
         - 여기서 4와 2를 꺼내 진행이 되는 연산은 아래와 같다.
           즉, 먼저 꺼낸 숫자가 오른쪽, 나중에 꺼낸 숫자가 왼쪽에 위치한다. (덧셈, 뺄셈에서 중요.)
           - 2 * 4 (4 * 2 가 아니다.)

      3) [ ][ ][ ][ ][ ]
         [11][ ] (스택)


    - PostCalculator.h     // EvalRPNExp 함수 선언
    - PostCalculator.c     // EvalRPNExp 함수 정의
    - PostCalculatorMain.c // 후위 표현식 계산 테스트 메인
    - ListBaseStack.h      // 스택 활용
    - ListBaseStack.c

    > 최종 프로그램
    
      - main 함수 : InfixCalculatorMain.c
      - 스택 활용 : ListBaseStack.h, ListBaseStack.c
      - 중위 표기법 수식 계산 : InfixCalculator.h, InfixCalculator.c
        - EvalInfixExp();
          - 후위 표기법으로 변환  : InfixToPostfix.h, InfixToPostfix.c
            - ConvToRPNExp();
          - 후위 표기법 수식 계산 : PostCalculator.h, PostCalculator.c
            - EvalRPNExp();




