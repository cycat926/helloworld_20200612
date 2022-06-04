# 리눅스 명령어와 매크로 사용법
1) **리눅스 명령어**
+ top
+ ps
+ jobs
+ kill
2) **vim 에디터에서 매크로 사용법**

---
## 리눅스 명령어
### **top**
![image](https://user-images.githubusercontent.com/106860798/172018319-693b9b02-1d3d-4f49-a64e-6d7c70d76c28.png)
#### 정의
> 리눅스 우분투에서 '*top 명령어*'를 사용하면 시스템 사용량을 실시간으로 확인할 수 있다.
top 명령어는 리눅스 시스템이 실행되고 난 후 지금까지의 시간과 시스템에 로그인된 사용자 수 그리고 시스템 부하율을 표시하는 명령어인 uptime의 결과를 가장 상단에 표시해주며, 그 아래로 프로세스 수치, CPUC 정보, 메모리 정보를 보여주고, 각 프로세스 별 부하율과 사태를 표시해준다.
#### 사용 구문
`top [옵션]`
#### top 출력 결과 설명
**첫째줄** :현재 시간을 표시해 준다.

**둘째줄** :총 수행중인 프로세스의 수와 실행중인 프로세스의 수가 나타난다.

**세번째줄** :cpu사용률을 볼 수 있다.

- us:사용자 레벨의 cpu 사용 비중
- sy:시스템 레벨의 cpu 사용 비중
- ni:우선순위가 낮은 프로세스의 cpu사용 비중
- id:유휴 상태의 cpu 사용 비중
- wa:I/O를 대기 중인 cpu사용률
- hi:interrupt handler에서 사용 중인 cpu 사용률, 빠르게 수행을 마쳐야 하는 작업
- si: hi에서 오래 걸리는 작업 때문에 미뤄놓은 작업
- st: 하이퍼바이저가 다른 가상 프로세서를 서비스하는 동안 가상 cpu가 실제 cpu를 기다리는 시간

**네다섯번째줄** :메모리관련 정보
#### 프로세스 상태 정보
|이름|설명|
|:---:|:---:|
|pid |프로세스 id|
|user| 프로세스를 실행시킨 사용자id|
|ni| nice값. 일의 nice value값이다. 마이너스를 가지는 nice value는 우선순위가 높음|
|virt |가상 메모리의 사용량|
|res |현재 페이지가 상주하고 있는 크기|
|shr| 분할된 페이지, 프로세스에 의해 사용된 메모리를 나눈 메모리의 총합|
|s |프로세스의 상태|
|%CPU |프로세스가 사용하는 CPU의 사용율|
|%MEM |프로세스가 사용하는 메모리의 사용율|
|COMMAND| 실행된 명령어|

#### top 명령어 옵션
|옵션|설명|
|:---:|:---:|
||옵션 없이 명령어를 실행하면 interval 간격(기본 3초)으로 화면을 갱신하며 정보를 보여준다.|
|-b|-b 옵션을 사용해 순간의 정보를 확인할 수 있다.|
|-n 2|-n 옵션을 사용하여 top 실행 주기를 2번 반복하도록 한다.|
|-q|시간의 간견 없이 계속하여 업데이트 정보를 출력한다.|
|-d delay|지정한 시간(delay 초)의 간격으로 정보를 업데이트하여 출력한다.|

#### top 실행 후 명령어
|명령어|설명|
|:---:|:---:|
|shift + p |CPU 사용률 내림차순|
|shift + m |메모리 사용률 내림차순|
|shift + t | 프로세스가 돌아가고 있는 시간 순|
|k | kill, k 입력 후 PID 번호 작성. signal은 9|
|f | sort field 선택 화면 -> q 누르면 RES순으로 정렬|
|a | 메모리 사용량에 따라 정렬|
|l | CPU Core별로 사용량 보여준다.|
|c |명령어 대신 명령어 라인을 보여줌|
|h| 도움말|
|s|보안 모드 작동|
|m|메모리 사용률 시각화 표시|
|H|상단의 Tasks기준을 쓰래드로 변경|
|u|모니터링할 user를 선택하여, 해당 권한 프로세스 감시|
|space|화면갱신|
|d|업데이트 간격을 조정|
|Z|화면 출력 색상 변경|
|z|Z로 변경된 출력 색상와 기본 출력 색상간 전환|
|B|글자 두껍게|
|q|top 종료|


#### top 명령어 페이지 이동
|명령어|설명|
|:---:|:---:|
|Page Down|프로세스의 다음페이지 목록|
|Page Up|프로세스의 이전페이지 목록|

***

### **ps**
![image](https://user-images.githubusercontent.com/106860798/172019446-33e0b058-f1f7-4c6b-bcbb-83bb35f11291.png)

#### 정의
> 리눅스 os관리 시 프로세스를 확인하고 싶은 경우 '*ps명령어(Process Status)*'를 사용한다. ps명령어는 현재 실행중인 프로세스 목록을 보여준다. 아파치, 오라클 등 프로그램 프로세스가 정상적인지 확인하거나 비정상적인 프로세스가 올라왔는지 확인 하는 등 리눅스 관리 전반적으로 많이 사용되는 명령어이다. 주로 파이프라인, grep명령어와 함께 사용하여 특정 프로세스를 확인하는데 많이 사용된다.
#### 사용 구문
`ps [옵션]`
#### ps 명령어 출력 항목
|항목|설명|
|:---:|:---:|
|USER (BSD)  UID (System V)|프로세스 소유자의 이름|
|PID|프로세스의 식별 번호|
|PPID|부모 프로세스의 PID|
|%CPU|CPU 사용 비율의 추정치 (BSD)|
|%MEM|Memory 사용 비율의 추정치(BSD)|
|VSZ|K 단위 또는 페이지 단위의 가상 메모리 사용량|
|RSS|실제 메모리 사용량|
|TTY|프로세스와 연결된 터미널|
|S (System V)  STAT (BSD)|현재 프로세스의 상태 코드|
|TIME|총 CPU 사용 시간|
|COMMAND|프로세스의 실행 명령행|
|STIME|프로세스가 시작된 시간 혹은 날짜|
|C (System V)  CP (BSD)|짧은 기간 동안의 CPU 사용률|
|F|플래그|
|PRI|실제 실행 우선순위|
|NI|nice 우선순위 번호|

#### ps 명령어 
|명령어|설명|
|:---:|:---:|
||pid, cmd 등 기본적인 내용만 출력된다. 옵션 없이는 잘 사용되지 않는다.|
|-f|uid(user ID), pid(process ID), ppid(patent ID), TTY(프로세스와 연결된 터미널) 등을 표시해준다.|
|-l|풀 포맷정보 외에 F(프로세스 플래그), S(프로세스 상태), PRI(우선순위) 등 더 많은 정보를 보여준다.|
|-p l|프로세스 번호가 1인 프로세스를 출력해준다. -e옵션과는 같이 사용할 수 없고 ps도 주로 grep과 함께 사용하므로 잘 사용되지 않는 옵션이다.|
|-u apache|apache 계정의 프로세스정보를 출력해주고 있다.|
|-e|숨겨진 프로세스까지 모두 보여준다. 매우 많이 나오기 때문에 more 명령어를 이용하여 보면 좋다.|
|-A|모든 프로세스를 보여준다.|
|-d |세션 리더를 제외한 모든 프로세스를 보여준다.|
|-a|세션 리더를 제외하고 데몬 프로세스처럼 터미널에 종속되지 않은 모든 프로세스를 출력한다.|
|-o|출력 포맷을 지정한다.|
|-m|프로세스뿐만 아니라 커널 스레드도 출력한다.|


#### ps 명령어 응용 예시
`ps -ef | more`

모든 프로세스를 풀 포맷으로 보여준다, more명령어를 줘서 페이지단위로 출력한다. 보통 grep으로 찾을 수 없을 때 수동으로 전체 프로세스를 보고자 하는경우 사용한다.
![image](https://user-images.githubusercontent.com/106860798/172019372-7b28de92-6884-4951-a1a4-1270b1dd5513.png)

 `ps -ef | grep apache`
 
가장 많이 사용되는 형태로 파이프라인을 이용하여 특정 패턴이 있는 프로세스를 찾아 낼 수 있다.주로 oracle 프로세스가 올라와있는지, apache 프로세스가 올라와있는지 등 특정 프로세스가 정상적으로 올라와 있는지 확인하는데 사용된다.
![image](https://user-images.githubusercontent.com/106860798/172019393-48a01958-f339-46f0-ae23-f5fd4ea43005.png)

`ps -el`

프로세스의 정보가 긴 포맷으로 출력된다. -ef 옵션에서 보지 못한 F,S,PRI,NI등 다양한 정보가 출력된다.
![image](https://user-images.githubusercontent.com/106860798/172019428-3b476ea6-6324-455b-9d83-460a010ef5b1.png)

---

#### ps와 top의 차이점
ps는 ps한 시점에 proc에서 검색한 cpu 사용량을 출력한다.
top은 proc에서 일정 주기로 합산해 cpu 사용율을 출력한다.

---

### **jobs**
![image](https://user-images.githubusercontent.com/106860798/172019771-0767ce95-69a1-4664-b993-a2856ddc72a4.png)
#### 정의
>리눅스 명령어 '*jobs*'는 작업이 중지된 상태, 백그라운드로 진행 중인 작업 상태, 변경 되었지만 보고되지 않은 상태 등을 표시하는 명령어이다. 
#### 사용 구문
`jobs [옵션] [job ID]`
#### jobs 명령어 옵션
|명령어|설명|
|:---:|:---:|
|-l|프로세스 그룹 ID를 state 필드 앞에 출력한다.|
|-n|프로세스 그룹 중에 대표 프로세스 ID를 출력한다.|
|-p|각 프로세스 ID에 대해 한 행씩 출력한다.|
|command|지정한 명령어를 실행한다.|
#### jobs로 알 수 있는 세션의 상태 값
|명령어|설명|
|:---:|:---:|
|Running|작업이 일시 중단되지 않았고 종료하지 않고 계속 진행 중임|
|Done|작업이 완료되어 0을 반환하고 종료 했음을 의미|
|Done(code)|작업이 정삭적으로 완료되었으며, 0이 아닌 코드를 반환 했음을 의미|
|Stopped|작업이 일시 중단|
|Stopped(SIGTSTP)|SIGTSTP 신호가 작업을 일시 중단|
|Stopped(SIGSTOP)|SIGSTOP 신호가 작업을 일시 중단|
|Stopped(SIGTTIN)|SIGTTIN 신호가 작업을 일시 중단|
|Stopped(SIGTTOU)|SIGTTOU 신호가 작업을 일시 중단|

---

### **kill**
![Screenshot_20220605-032909_Chrome](https://user-images.githubusercontent.com/106860798/172020963-2a86a08e-7d43-49dc-b1cd-12cb86fce99e.jpg)

#### 정의
>'*kill명령어*'는 프로세스에 특정한 signal을 보내는 명령어로 일반적으로 종료되지 않는 프로세스를 종료 시킬 때 많이 사용한다.
#### 사용 구문
`kill [옵션 or 시그널] PID`
#### kill 명령어 옵션
|명령어|설명|
|:---:|:---:|
|-l|지원하는 시그널의 목록을 확인할 수 있다.|
|-SIGHUP (1) |로그아웃 등의 접속을 끊을 때 발생 하는 시그널 입니다. 실행 중인 프로세스가 이용하는 config 파일을 변경 후 갱신할 때 발생 되기도 한다.|
|-SIGINT (2) | 현재 실행 중인 프로세스의 동작을 멈출 때 사용한다.|
|-SIGQUIT (3) | 터미널에서 Ctrl C 를 입력할 때 발생하는 시그널 입니다. 비정상 종료에 해당된다.|
|-SIGKILL (9) | 무조건 해당 프로세스를 중단 시킨다.|
|-SIGSEGV (11) | 메모리 액세스가 잘못 될 경우 발생된다.|
|-SGTERM (15) | 실행 중인 프로세스를 정상 종료 시킨다.|
|-CONT (18) | Continue. Stop등에 의해 정지된 프로세스를 다시 실행시킨다. |
|-STOP (19) | 무조건적, 즉각적으로 정지시킨다.|
|-TSTP (20) |실행 정지 후 다시 실행을 계속하기 위하여 대기시키는 시그널 [CTRL] + [Z] 를 눌렀을 때 보내지는 시그널이다.|

---

## **vim 에디터에서 매크로 사용법**
### 매크로의 정의
vim 에서 '*매크로*'라는 단어는 다음을 나타낼 수 있다.
- 레지스터에 기록된 명령 시퀀스
- 형식화된 키 시퀀스를 더 긴 스퀀스로 확장하기 위한 매핑
- vim 스크립트 언어로 작성된 스크립트

일반적인 의미의 매크로는 같은 동작을 반복하게 해주는것을 의미한다.
### 매크로 기록방법
1) vim 에디터의 명령모드에서 q를 누루면 매크로가 실행된다.
2) q를 누룬다음 매크로의 이름으로 사용할 알파벳을 누른다. 예를 들어 qa라고 누르면 a라는 이름의 매크로가 기록되기 시작하고 ab라고누르면 b라는 이름의 매크로가 기록되기 시작한다. 
3) 기록이 끝났으면 다시 명령모드에서 q를 누른다.
### 매크로 재생방법
1) 명령모드에서 @a라고 누르면 매크로a가 재생된다.
2) @@를 누르면 제일 마지막에 재생된 매크로가 실행된다.예를 들어 가장 최근에 @v를 했다면 @@때 재생되는 매크로는 v가 된다.
### 매크로를 파일로 저장하는 방법
1) ~/.vimrc 파일을 연다.
2) 매크로 이름을 b라고 짓고 싶으면 let @b=' 까지 친 다음에 insert모드에서 Ctrl-R Ctrl-R b를 누르면 매크로 b의 내용물이 입력된다.
3) 내용물이 입력 되었으면 '를 마저 닫아준다.
---
