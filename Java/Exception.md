 |CheckedException|UncheckedException|
|----|---|
|RuntimeException을 상속받지 않은 Exception 클래스의 하위 클래스들 <br> try/catch 또는 throw를 사용해서 반드시 에러를 처리해야 함|RuntimeException 상속|
|컴파일 단계에서 확인|실행 단계에서 확인|
|롤백 안됨|롤백 됨|
|ex) IOException|ex) NullPointerException, IndexOutOfBoundsException|
