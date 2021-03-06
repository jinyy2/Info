# CPU Scheduling

:  운영 체제는 프로세스들에게 CPU 등의 자원 배정을 적절히 함으로써 시스템의 성능을 개선할 수 있다.



## 선점 스케줄링(Preemptive)

: CPU를 점유하는 작업이 있을 때 우선 순위가 높은 프로세스는 강제로 CPU를 점유할 수 있다. (I/O, Event wait)

| 프로세스 PID | 실행시간 |
| :----------: | :------: |
|      p1      |    30    |
|      p2      |    50    |
|      p3      |    20    |

time out : 10



### 1. SRT(Shortest Remaining Time)

: 프로세스의 실행시간이 가장 적게 남아있는 것부터 실행

```
|-p3-|-p1-|-p2-|
0---20---50---100

평균실행시간 : (20+30+50)/3
평균대기시간 : (0+20+50)/3
평균반환시간 : (20+50+100)/3
```





### 2. 라운드 로빈(Round-Robin)

- 시분할 시스템
- 시간 제한이 있음
- Timeout이 길어질 경우 FCFS와 비슷

```
|-p1-|-p2-|-p3-|-p1-|-p2-|=p3=|=p1=|=p2=|
0---10---20---30---40---50---60---70---100
완료 p3 p1 p2
```



### 3. 다단계 큐(Multi-level Queue)

- 프로세스의 우선 순위에 따라 대기하는 큐를 다르게 배정

  

### 4. 다단계 피드백 큐(Multi-level Feedback Queue)

- 다단계 큐 방식에서 오래 대기한 프로세스가 높은 레벨의 대기 큐로 이동







## 비선점 스케줄링(Non-Preemtive)

: 할당된 자원을 다른 프로세스가 뺐을 수 없음 (Interrupt, Scheduler Dispatch)

| 프로세스 PID | 실행시간 | 대기시간 |
| :----------: | :------: | -------- |
|      p1      |    30    | 40       |
|      p2      |    50    | 30       |
|      p3      |    20    | 20       |



### 1. HRN(Highest Response ratio Next)

- SJF의 단점을 보안

- 우선순위 계산 (숫자가 높을수록 우선순위가 높음)

  우선순위 = (대기시간 + 실행시간) / 실행시간

  

```
p1 = (30+40)/30 = 2.3
p2 = (50+30)/50 = 1.6
p3 = (20+20)/20 = 2


|-p1-|-p3-|-p2-|
0---30---50---100

평균실행시간 : (30+20+50)/3
평균대기시간 : (0+30+50)/3
평균반환시간 : (30+50+100)/3
```



### 2. SJF(Shrotest Job First) : 단기 작업 우선

- Reday Queue에서 실행시간이 가장 작은 프로세스 우선
- 가장 적은 평균 대기시간
- 실행 시간이 긴 프로세스는 무한 대기 상태가 발생

```
|-p3-|-p1-|-p2-|
0---20---50---100

평균실행시간 : (20+30+50)/3
평균대기시간 : (0+20+50)/3
평균반환시간 : (20+50+100)/3
```



### 3. Priority

- 프로세스마다 우선순위를 부여함

- 우선순위가 낮을 경우 기아상태가 일어남

- 우선순위가 낮은 작업은 무한 대기 상태가 발생

  

### 4. Deadline

- 프로세스에게 일정한 시간을 줌



### 5. FCFS(First Come First Service) : 선입선출

```
|-p1-|-p2-|-p3-|
0---30---80---100

평균실행시간 : (30+50+20)/3
평균대기시간 : (0+30+80)/3
평균반환시간 : (30+80+100)/3
```

