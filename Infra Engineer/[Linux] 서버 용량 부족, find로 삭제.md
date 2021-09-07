# [Linux] 서버 용량 부족, find로 삭제



---

**Issue** : [서버 용량 부족] 개발 서버의 로그 폴더 용량이 99%이상으로 가득차 WAS 로그를 저장할 파일 여유공간 부족
**Solution** : 용량을 많이 차지하는 로그 폴더의 파일 삭제
**Command** : find, mtime, exec 

---



### 디렉터리 구성 

- /logs/lena/Instance1

- /logs/lena/Instance2

- /logs/lena/Instance3

- /logs/lena/Instance4
  …



### Command

```
$ df -h # disk free(디스크 여유 공간 확인) => 리눅스 시스템 전체의 마운트 된 디스크 사용량 확인
$ du -h . # disk usage(디렉터리 디스크 사용량 확인)
$ find . -type f -mtime +7 -name “**log**” -ls -exec rm {} \;
```



`find .` : 찾아라 현재위치부터
`-type f` : 타입이 파일인
`-mtime +7` : 파일의 마지막 변경시간이 7일이 지난
`-name “*log*”` : 이름에 log가 들어간
`-ls` : 파일의 목록 확인
`-exec rm {} \;` : 나온 값들을 제거



#### 주의할 것

-mtime -7 을 해버릴 경우 7일 지난이 아닌 7일 이내 파일을 삭제하여 큰일을 초래할 수 있다.



> atime : 파일의 마지막 접근 시간
> ctime : inode changed time
> mtime : 파일의 마지막 변경 시간