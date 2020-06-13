# Git Commit Convention

## 1. Commit Message
```
[Type] subject

body

footer
```
Example
```
[Fix] 날짜 형식 검증 추가

DateCheck.java: 24번째 라인에서 날짜 형식을 추가하지않아, NPE를 내던 오류를 수정합니다. (fix #31)

Issue #31
```

## 2. Commit Type
* Feat : 기능추가
* Fix : 버그 수정
* Misc : 문서 수정, 리소스 추가 등
* Refactor : 코드 리팩토링
* Test : 테스트 
* Style : 소스에 영향없는 코드 수정 (공백, 포맷, 세미콜론 누락 등,,,)
* Perf : 성능 향상을 위한 코드 수정
* Ci : CI 설정 변경
* Build : 의존성 변경 혹은, 빌드 시스템 변경 (gulp, npm 등..)

## Subject (Required)
* 제목은 <b>50</b>자 이내로 작성한다
* 영문일 경우 첫글자를 대문자로 시작한다
* 제목 끝에 .은 쓰지 않는다
* 명령조로 작성한다

## Body (Not Required)
* 부연설명이 필요하거나, 이유가 필요할때 기록한다
* 무엇을, 왜 수정했는지에 대해 기록한다
* 영문 기준 <b>72자</b>마다 줄을 바꾼다 


## Footer (Not Required)
* 선택사항임으로 무조건 적을 필요가 없다
* Issue tracker id를 적거나, Github 이슈 종료를 위해 사용한다

Example
```
[Fix] 날짜 형식 검증 추가

DateCheck.java: 24번째 라인에서 날짜 형식을 추가하지않아, NPE를 내던 오류를 수정합니다. 

Issue #31, fixed #31, close #30
```


## Issue auto closed command
* close
* fix
* resolve
해당 커맨드의 복수형이나, 과거형을 포함해서 git commit 메세지에 적으면 자동으로 종료된다.



### 참조 
[좋은 git 커밋 메시지를 작성하기 위한 7가지 약속](https://meetup.toast.com/posts/106)<br>
[Angular Commit Message Guidelines](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#-commit-message-guidelines)