# 숫자 야구 게임
## 진행 방법
* 숫자 야구 게임 요구사항을 파악한다.
* 요구사항에 대한 구현을 완료한 후 자신의 github 아이디에 해당하는 브랜치에 Pull Request(이하 PR)를 통해 과제를 제출한다.

## 과제 제출 과정
* [과제 제출 방법](https://github.com/next-step/nextstep-docs/tree/master/precourse)

- [x] 프로젝트를 자신의 계정으로 fork한다. 저장소 우측 상단의 fork 버튼을 클릭해 fork한다.
- [x] fork한 저장소를 자신의 컴퓨터로 clone한 후 폴더로 이동한다.
```
git clone https://github.com/{본인_아이디}/{저장소 아이디}.git
```
- [x] 기능 구현을 위한 브랜치 생성
```
git checkout -b 브랜치이름
```
- [x] 통합개발도구(Eclipse 또는 IntelliJ)로 가져오기(import)
- [ ] 기능 구현
- [ ] 기능 구현 후 add, commit
```
git status // 변경된 파일 확인
git add -A(또는 .) // 변경된 전체 파일을 한번에 반영
git commit -m "메시지" // 작업한 내용을 메시지에 기록
```
- [ ] 본인 원격 저장소에 올리기
```
git push origin 브랜치이름
```
- [ ] github 서비스에서 pull request를 보낸다.

- [ ] 메일 보내기
```
To. edu.nextstep@gmail.com

제목 : [$이름] 프리코스 미션 제출합니다.
내용 : 
다음 두 개의 정보를 반드시 포함해 메일을 보낸다.

* 교육 과정 신청시 email 주소: 
* Pull Request URL: 

미션을 진행하면서 느끼고, 배운점, 많은 시간을 투자한 부분 등도 포함하면 더 좋을 것 같아요.
```

## 기능 요구사항
```text
- 기본적으로 1부터 9까지 서로 다른 수로 이루어진 3자리의 수를 맞추는 게임이다.
- 같은 수가 같은 자리에 있으면 스트라이크, 다른 자리에 있으면 볼, 같은 수가 전혀 없으면 포볼 또는 낫싱이란 힌트를 얻고, 그 힌트를 이용해서 먼저 상대방(컴퓨터)의 수를 맞추면 승리한다.
    - [예] 상대방(컴퓨터)의 수가 425일 때, 123을 제시한 경우 : 1 스트라이크, 
    456을 제시한 경우 : 1 스트라이크 1볼, 
    789를 제시한 경우 : 낫싱

- 위 숫자 야구게임에서 상대방의 역할을 컴퓨터가 한다. 
    - 컴퓨터는 1에서 9까지 서로 다른 임의의 수 3개를 선택한다. 
    - 게임 플레이어는 컴퓨터가 생각하고 있는 3개의 숫자를 입력하고, 컴퓨터는 입력한 숫자에 대한 결과를 출력한다.

- 이 같은 과정을 반복해 컴퓨터가 선택한 3개의 숫자를 모두 맞히면 게임이 종료된다. 
- 게임을 종료한 후 게임을 다시 시작하거나 완전히 종료할 수 있다.
```

## 프로그래밍 요구사항
- **메서드 분리**
    - [자바 코드 컨벤션](https://naver.github.io/hackday-conventions-java/)
    - indent depth를 2가 넘지 않도록 구현 **1까지만 허용**
    - else에 해당하는 문법을 사용하지 않는다.
    - 메서드의 길이가 10라인을 넘어가지 않도록 구현

## 기능 목록 및 시나리오 작성
- [x] 전체 게임 반복
    - [x] 컴퓨터 차례 
        - [x] **1 ~ 9**까지 **서로 다른 임의의 수 3**개 생성

    - [x] 게임 플레이어 차례
        - [x] 게임 플레이어는 컴퓨터가 입력한 3개의 숫자를 추정하여 입력
            - [x] 유효성 검사 입력 값의 길이가 3인지 확인
            - [x] 유효성 검사 입력 값이 숫자로 변롼이 가능한지 확인
            - [x] 유효성 검사 입력 값이 1 ~ 9까지 범위의 숫자인지 확인

        - [x] 사용자가 입력한 값과 컴퓨터가 입력한 숫자에 대한 비교
            - 조건
                - [x] 숫자와 순서가 일치하는 경우 스트라이크
                - [x] 숫자가 일치하나 순서가 맞지 않는 경우 볼
                - [x] 게임플레이어가 입력한 값이 컴퓨터가 입력한 값에 포함되지않은 경우 낫싱

    - [x] 3스트라이크로 인하여 한 회 게임 종료 후 다시 시작 여부 입력에 따른 재시작 및 종료
        - 사용자가 입력한 값에 대한 유효성 검사
            - [x] 입력한 값이 1 또는 2가 아닌경우 다시 입력
        - [x] 1를 입력한 경우 처음부터 다시 시작 
        - [x] 2를 입력한 경우 프로그램 종료

## 테스트 코드 목록
- 정상 응답
    - [x] 컴퓨터 선택 - 컴퓨터가 생성한 **값의 길이가 3**인지 확인
    - [x] 플레이어 선택 - 게임 플레이어가 입력한 **문자열의 길이 값이 3인지 확인**
    - [x] 플레이어 선택 - 게임 플레이어가 입력한 **문자열이 정수형으로 변환되는지 확인**
    - [x] 플레이어 선택 - 게임 플레이어가 입력한 값을 **정수형 배열로 변환이 가능한 지 확인**
    - [x] 플레이어 선택 - 게임 플레이어가 **입력한 값이 정상적으로 입력되어 정수형 배열로 변환이 되었는지 확인**
    - [x] 재시작 기능 - 사용자가 입력한 값이 1 또는 2가 입력되었는지 확인

- 예외 응답
    - [x] 플레이어 선택 - 사용자의 입력한 문자열의 **길이 값이 3이 아닌 경우 예외**
    - [x] 플레이어 선택 - 게임 플레이어가 입력한 값을 **숫자로 변환 시 예외**
    - [x] 플레이어 선택 - 사용자의 입력한 각 값이 **1 ~ 9까지 범위의 정수형이 아닌 경우 예외**
    - [x] 재시작 기능 - 플레이어가 입력한 값이 1 또는 2가 아닌 경우 예외

## 리펙토링
- 메인 로직을 실행하는 클래스, 게임 로직 클래스 생성
- TDD로 진행하기 위해 Scanner를 메서드 안에서 생성 및 입력 받지 않고 파라미터로 전달받아 처리할 수 있도록 수정

## ISSUE
```
No tests found for given includes
```
[solve](https://stackoverflow.com/questions/55405441/intelij-2019-1-update-breaks-junit-tests)

