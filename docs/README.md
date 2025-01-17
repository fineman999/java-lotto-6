# 1. 학습 목표
- 자바 code convention을 지키면서 프로그래밍하는 경험
- JUnit 사용법을 익혀 단위 테스트하는 경험
- 학습테스트를 하면서 JUnit 사용법을 익히는 방법
- 메소드를 분리하는 리펙터링 경험
- 함수(또는 메서드)의 길이가 15라인을 넘어가지 않도록 구현
---

# 2. 프로그래밍 요구사항

- 함수(또는 메서드)의 길이가 15라인을 넘어가지 않도록 구현한다. 
  - 함수(또는 메서드)가 한 가지 일만 잘 하도록 구현한다.
- else 예약어를 쓰지 않는다.  
- Java Enum을 적용한다.
- 도메인 로직에 단위 테스트를 구현해야 한다.
- indent(인덴트, 들여쓰기) depth를 3이 넘지 않도록 구현한다. 2까지만 허용한다.
- 3항 연산자를 쓰지 않는다.
- 함수(또는 메서드)가 한 가지 일만 하도록 최대한 작게 만들자.

# 기능 구현
## 핵심 도메인
### Lotto 번호
- [x] 로또 번호의 숫자 범위는 1~45 제한
- [x] 1~45 범위를 벗어나면 예외 발생
- [x] 1~45 범위 내의 숫자만 입력
- [x] 6개의 숫자를 입력
- [x] 중복된 숫자가 입력되면 예외 발생
- [x] 입력받은 숫자를 반환

### Bonus 번호
- [x] 보너스 번호의 숫자 범위는 1~45 제한
- [x] 1~45 범위를 벗어나면 예외 발생
- [x] 1~45 범위 내의 숫자만 입력
- [x] 1개의 숫자를 입력
- [x] 입력받은 숫자를 반환

### 로또 용지
- [x] 로또번호와 보너스번호를 입력
- [x] 랜덤한 로또와 보너스 이벤트일 경우 필드값에 있는 당첨 로또 번호와 보너스 번호를 랜덤한 로또 번호와 보너스 번호와 비교후 맞는 숫자만큼 반환
- [x] 랜덤한 로또일 경우 필드값에 있는 당첨 로또 번호를 랜덤한 로또 번호와 보너스 번호와 비교후 맞는 숫자만큼 반환

### 금액 
- [x] 로또 구매 금액을 입력받기
- [x] 로또 구매 금액을 1000원 단위로 입력
  - [x] 1000원 단위가 아닐 경우 예외 발생
- [x] 로또 구매 금액을 입력받은 금액만큼 로또를 생성
- [x] 로또 구매 개수 반환
- [x] 로또 구매 금액 반환

### 랜덤 로또 생성기
- [x] 랜덤한 로또을 만들 수 있는 RandomGenerator와 구매 금액 입력
- [x] 로또 구매 개수만큼의 랜덤한 로또 반환
- [x] 랜덤한 6개의 값을 출력하는 RandomGenerator와 구매 개수를 입력받아 랜덤한 로또 생성


## 프록시 - chain of responsibility 패턴

### 상금
- [x] 상금을 입력
- [x] 상금을 반환

### 번호 맞추기
- [x] 몇개의 맞출 경우 상금을 받을지 개수 입력
- [x] 몇개의 맞출 경우 상금을 받을지 개수 반환

### 상금 계산 - chain of responsibility 패턴
- [x] 주어진 복권 번호와 당첨 번호를 비교하고, 일치하는 경우 다음 처리기에게 전달
- [x] 현재까지의 총 상금 횟수를 반환
- [x] 투자 금액에 대한 수익률을 계산하여 반환
- [x] 당첨 통계를 문자열 형태로 반환

## 게임 진행
- [x] 사용자로부터 당첨 번호를 입력받아 winningNumbers 필드를 초기화
- [x] 사용자로부터 보너스 번호를 입력받아 bonusNumber 필드를 초기화
- [x] winningNumbers와 bonusNumber를 기반으로 사용자의 복권 번호를 생성하여 paper 필드를 초기화
- [x] 사용자로부터 투자 금액을 입력받고, 랜덤으로 복권 번호를 생성하여 lottery 필드를 초기화
- [x] 보너스 볼이 설정되었는지 확인하고, 설정되지 않았으면 true를 반환
- [x] 복권이 생성되었는지 확인하고, 생성되지 않았으면 true를 반환
- [x] 당첨 번호가 설정되었는지 확인하고, 설정되지 않았으면 true를 반환
- [x] 사용자의 복권 번호가 생성되었는지 확인하고, 생성되지 않았으면 true를 반환
- [x]lottery와 paper를 기반으로 당첨 결과를 계산하는데 사용됩니다. 결과는 prizeHandler를 통해 처리