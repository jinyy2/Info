

# Nginx 설치하기

### Nginx 설치 안된 경우

sudo apt update (패키지 목록 업데이트)

sudo apt upgrade (패키지를 최신으로 업그레이드)

sudo apt-get install ngingx 



### Nginx confing 설정

```
vi /etc/nginx/sites-available/default
```

npm run build 후에 나오는 dist파일의 위치 

```
root /home/ubuntu/project_name/front-end/dist;
```



**sudo nginx -t  (문법 체크)**

시작: **sudo systemctl start nginx**

종료: **sudo systemctl stop nginx**

재시작: **sudo systemctl restart nginx**



vue-router의 기본 설정:  hash 모드

URL 해시를 사용하기 때문에 URL이 변경될 때 페이지 Reload X

vi /etc/nginx/sites-available/default

```
location / {

	try_files $uri $uri/ /index.html;

}
```

***

참고URL: https://router.vuejs.org/guide/essentials/history-mode.html#example-server-configurations

***



## certbot 설치

Ubuntu 186u,

저장소 설정 및 업데이트 진행

```
$ sudo apt-get update
$ sudo apt-get install software-properties-common
$ sudo add-apt-repository universe
$ sudo add-apt-repository ppa:certbot/certbot
$ sudo apt-get update
```



certbot설치

```
$ sudo apt-get install certbot python3-certbot-nginx
```





## Nginx 세팅

```
sudo vim /etc/nginx/sites-available/default
```

```
server_name www.selfdomain.com;
```



```
sudo nginx -t
```

```
sudo systemctl restart nginx
```





## SSL 인증 획득 (재변경 가능)

```
sudo certbot --nginx -d ww.selfdomain.com
```

1. No redirect
2. Redirect



## 인증서 자동갱신

```
$ sudo certbot renew --dry-run
```



Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/domain_name/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/domain_name/privkey.pem
   Your cert will expire on 2020-11-10. To obtain a new or tw

***

참고 URL: https://twpower.github.io/44-set-free-https-by-using-letsencrypt

***



## Spring boot https 적용



openssl pkcs12 - export -in  fullchain.pem -inkey privkey.pem

 -out keystore.12 -name airpageserver -CAfile chain.pem -caname root



server.ssl.key-store=keystore.p12
server.ssl.key-store-type=PKCS12
server.ssl.key-store-password=123456
server.ssl.key.alias=spring