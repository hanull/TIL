# Statement vs PreparedStatement
SQL 구문을 실행하는 역할을 하는 인터페이스

- Statement
    - static
        - 문장을 작성할 때 매개변수를 전달하지 않고 하나를 수행하는데 사용한다. 즉 쿼리문에 값이 미리 입력되어 있어야 한다.
    - slow execution
        - 사전 컴파일되지 않고, 특정 쿼리를 실행하는 데 더 많은 시간이 걸린다.
    - Doesn't prevent SQL Insection

- PreparedStatement
    - dynamic
    - faster execution
        - 쿼리를 수행하기 전에 이미 컴파일 되어 있어 빠르다.
    - helps prevent SQL Insection 


반복적인 실행이 필요없는 쿼리이고 자주 사용되지 않는 쿼리라면 statement 를 사용

PreparedStatement를 잘 활용하면 CPU 사용량을 줄이고 DB에 접근하는 소프트웨어의 속도를 향상시키는 효과가 있다
