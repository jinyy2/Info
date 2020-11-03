# AWS (Amazon Web Server)

아마존 웹 서비스는 다른 웹 사이트나 클라이언트측 응용 프로그램에 대해 온라인 서비스를 제공하고 있다. 이러한 서비스의 상당수는 최종 사용자에 직접 공개되는 것이 아니고, 다른 개발자가 사용 가능한 기능을 제공하는 플랫폼을 제공하는 [PaaS](https://ko.wikipedia.org/wiki/PaaS)이다.



**아마존 일래스틱 컴퓨트 클라우드**(Amazon Elastic Compute Cloud, EC2)는 [아마존닷컴](https://ko.wikipedia.org/wiki/아마존닷컴)의 [클라우드 컴퓨팅](https://ko.wikipedia.org/wiki/클라우드_컴퓨팅) 플랫폼 [아마존 웹 서비스](https://ko.wikipedia.org/wiki/아마존_웹_서비스)의 중앙부를 이루며, 사용자가 [가상 컴퓨터](https://ko.wikipedia.org/wiki/가상_컴퓨터)를 임대 받아 그 위에 자신만의 컴퓨터 애플리케이션들을 실행할 수 있게 한다.



## [SSH 클라이언트를 사용하여 Linux 인스턴스에 연결](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)

```
$ ssh -i /path/my-key-pair.pem my-instance-user-name@my-instance-public-dns-name
ex) ssh -i ~/example.pem ubuntu@x.xx.xxx.xxx
```





## [PuTTY를 사용하여 Windows에서 Linux 인스턴스에 연결](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/putty.html)

PuTTY에서는 SSH 키의 프라이빗 키 형식을 기본적으로 지원하지 않는다.

PuTTYgen을 사용하여 .pem -> .ppk로 변환하기



키를 공개적으로 볼 수 없게 만들기

```
$ chmod 400 jinyy2.pem
```



### 타임존 변경

#### **변경 전**

`date`
Thu Oct 15 16:03:02 UTC 2020

```
$ sudo rm /etc/localtime
$ sudo ln -s /usr/share/zoneinfo/Asia/Seoul /etc/localtime
```

#### **변경 후**

`date` 

Fri Oct 16 01:04:19 KST 2020



## yarn 설치하기 

``` 
$ curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
$ echo "deb http://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list sudo apt update -y 
$ sudo apt install yarn
$ yarn --version
```



## npm 설치하기

```
$ sudo apt install npm 
$ npm -v
```



## Java 설치하기

### Java8

``` 
$ sudo apt-get update
$ sudo apt-get install openjdk-8-jdk
$ java -version
$ javac -version
```



> openjdk version "1.8.0_265"
> OpenJDK Runtime Environment (build 1.8.0_265-8u265-b01-0ubuntu2~18.04-b01)
> OpenJDK 64-Bit Server VM (build 25.265-b01, mixed mode)



### java8 설치 위치

``` /usr/lib/jvm/java-8-openjdk-amd64/
/usr/lib/jvm/java-8-openjdk-amd64/
```





# DOCKER

도커는 **컨테이너 기반의 오픈소스 가상화 플랫폼**입니다.

실행환경을 컨테이너로 추상화하고 동일한 인터페이스를 제공하여 프로그램의 배포 및 관리를 단순하게 해줍니다. 

>  https://subicura.com/2017/01/19/docker-guide-for-beginners-1.html









#### 컨테이너 확인

```
$ docker container ls
```



#### 실행중인 컨테이너 목록

```
$ docker ps -a
```



#### 컨테이너 중지하기 

```
$ docker ps # get container ID
$ docker stop ${TENSORFLOW_CONTAINER_ID}
$ docker ps -a # show all containers
```



#### 컨테이너 삭제

````
 $ docker rm `CONTAINER ID`
````

 

#### 이미지 확인

```
$ docker search mariadb 
```



#### mariadb 이미지 다운로드

```
$ docker pull mariadb
```



#### 설치된 images 확인

```
$ docker images
```



#### 설치된 image 삭제

```
$ docker rmi [IMAGE ID]
```



## Docker 설치

### 우분투에서 패키지로 도커 설치하기(둘 중 택1)



#### 1. 리눅스 배포판 종류를 자동으로 인식해 Docker 패키지를 설치

(둘 중 택 1)

```
$ sudo wget -qO- https://get.docker.com/ | sh
```

 ```
$ curl -fsSL https://get.docker.com/ | sudo sh
 ```



**sudo 없이 사용하기**

docker는 기본적으로 root권한이 필요합니다. root가 아닌 사용자가 sudo없이 사용하려면 해당 사용자를 `docker`그룹에 추가합니다.

```
$ sudo usermod -aG docker $USER # 현재 접속중인 사용자에게 권한주기
$ sudo usermod -aG docker your-user # your-user 사용자에게 권한주기
```



```
$ docker -v
> Docker version 19.03.13, build 4484c46d9d
```



```
$ cat /etc/group | grep docker
> docker:x:999:
```



```
$ sudo usermod -aG docker $USER # 현재 접속중인 사용자에게 권한주기
$ cat /etc/group | grep docker
> docker:x:999:ubuntu
```





#### 2. 우분투에서 패키지로 도커 설치하기

```
$ sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

- apt-transport-https : 패키지 관리자가 https를 통해 데이터 및 패키지에 접근할 수 있도록 한다.
- ca-certificates : ca-certificate는 certificate authority에서 발행되는 디지털 서명. SSL 인증서의 PEM 파일이 포함되어 있어 SSL 기반 앱이 SSL 연결이 되어있는지 확인할 수 있다.
- curl : 특정 웹사이트에서 데이터를 다운로드 받을 때 사용
- software-properties-common : *PPA를 추가하거나 제거할 때 사용한다.
  

```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add
```

- f : HTTP 요청 헤더의 contentType을 multipart/form-data로 보낸다.
- s : 진행 과정이나 에러 정보를 보여주지 않는다.(–silent)
- S : SSL 인증과 관련?
- L : 서버에서 301, 302 응답이 오면 redirection URL로 따라간다.
- apt-key : apt가 패키지를 인증할 때 사용하는 키 리스트를 관리한다. 이 키를 사용해 인증된 패키지는 신뢰할 수 있는 것으로 간주한다. add 명령어는 키 리스트에 새로운 키를 추가하겠다는 의미이다.
  


```
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
```

```
$ sudo apt update
```

- add-apt-repository : PPA 저장소를 추가해준다. apt 리스트에 패키지를 다운로드 받을 수 있는 경로가 추가된다.



```
$ apt-cache policy docker-ce
```

```
$ sudo apt install docker-ce
```







##  Docker에서 Maria DB 설치

```
$ sudo docker run --name `container-name` -p 3306:3306 -e MYSQL_ROOT_PASSWORD=`password` -d mariadb
```



### 컨테이너 Maria DB 접속하기

```
$ sudo docker exec -it `container-name` mysql -u root -p

password:`password`
```







참고~

#### 접근권한설정

EC2 인바운드 규칙 설정

![image-20201025223013379](/Users/jinyy2/Library/Application Support/typora-user-images/image-20201025223013379.png)

grant all privileges on *.* to 'root'@'%' identified by 'password';

create user 'root'@'%' identified by 'password';



## 데이터베이스 관리 툴 (DBeaver)

#### 새 데이터 베이스 연결 `MariaDB`

Server Host: `퍼블릭 IPv4 DNS` 

port : `3306`

Username: `mariadb id`

Password:  `mariadb password`



# Nginx 설치하기

```
$ sudo apt-get update (패키지 목록 업데이트)
$ sudo apt-get upgrade (패키지를 최신으로 업그레이드)
$ sudo apt-get install nginx  
```



## Nginx config 설정

```
$ sudo vi /etc/nginx/sites-available/default
```



### npm run build 후에 나오는 dist파일의 위치 

```
# Jenkins x
root /home/ubuntu/`project_name`/frontend/dist;

# Jenkins
root /var/lib/jenkins/workspace/`jenkins_item_name`/frontend/dist;
```



**sudo nginx -t  (문법 체크)**

시작: **sudo systemctl start nginx**

종료: **sudo systemctl stop nginx**

재시작: **sudo systemctl restart nginx**



```
$ npm i  #프로젝트 모듈 설치
$ npm run build #webpack사용하여 dist파일로 빌드
$ npm run serve 서버실행 (테스트)
```







vue-router의 기본 설정:  hash 모드

URL 해시를 사용하기 때문에 URL이 변경될 때 페이지 Reload X



```
$ sudo vi /etc/nginx/sites-available/default
location / {

	try_files $uri $uri/ /index.html;

}



```



***

참고URL: https://router.vuejs.org/guide/essentials/history-mode.html#example-server-configurations

***



# SSL: 보안 소켓 계층(Secure Sockets Layer, SSL)

SSL은 웹사이트와 브라우저(혹은, 두 서버) 사이에 전송된 데이터를 암호화하여 인터넷 연결을 보안을 유지하는 표준 기술입니다. 이는 해커가 개인 정보 및 금융 정보를 포함한 전송되는 모든 정보를 열람하거나 훔치는 것을 방지합니다.



## Certbot 설치

Ubuntu 186u,



### 저장소 설정 및 업데이트 진행

```
$ sudo apt-get update
$ sudo apt-get install software-properties-common
$ sudo add-apt-repository universe
$ sudo add-apt-repository ppa:certbot/certbot
$ sudo apt-get update
```



### certbot설치

```
$ sudo apt-get install certbot python3-certbot-nginx
```



### Nginx 셋팅

```
$ sudo vi /etc/nginx/sites-available/default
```

```
server_name www.example.com;
```



```
$ sudo nginx -t
```

```
$ sudo systemctl restart nginx
```





## SSL 인증 획득 (재변경 가능)

```
$ sudo certbot --nginx -d www.example.com
```

1. email : 암거나
2. agree
3. n
4. 1. No redirect
   2. **Redirect**

>Congratulations! Your certificate and chain have been saved at:
>**/etc/letsencrypt/live/k3b107.p.ssafy.io/fullchain.pem**
>Your key file has been saved at:
>**/etc/letsencrypt/live/k3b107.p.ssafy.io/privkey.pem**
>Your cert will expire on 2021-01-24. To obtain a new or tweaked
>version of this certificate in the future, simply run certbot again
>with the "certonly" option. To non-interactively renew *all* of
>your certificates, run "certbot renew"





### /etc/nginx/sites-available/default - 아래 사항이 추가 됨

```
listen [::]:443 ssl ipv6only=on; # managed by Certbot
listen 443 ssl; # managed by Certbot
ssl_certificate /etc/letsencrypt/live/k3b107.p.ssafy.io/fullchain.pem; # managed by Certbot
ssl_certificate_key /etc/letsencrypt/live/k3b107.p.ssafy.io/privkey.pem; # managed by Certbot
include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot
```



### live 안들어가질 때

```
$ cd /etc/letsencrypt/live/`server_name`/
$ ls -al
 > drwxr-xr-x   3 root root 4096 Oct 27 00:12 live  #권한 확인
$ sudo chmod 755 live
```

 

### 파일 목록

```
 $ cd /etc/letsencrypt/live/`server_name`/
  > README  cert.pem  chain.pem  fullchain.pem privkey.pem
```

- cert.pem: 도메인의 인증서
- chain.pem: Let’s Encrypt chain 인증서
- fullchain.pem: cert.pem + chain.pem
- privkey.pem: 인증서의 개인키



### 인증서 자동갱신 (기본 90일)

```
$ sudo certbot renew --dry-run
```





***

참고 URL: https://twpower.github.io/44-set-free-https-by-using-letsencrypt

***





## Spring boot https 적용



#### 현재 생성된 키로 keystore.p12를 만듦

```
$ cd /etc/letsencrypt/live/`server_name`/
$ sudo openssl pkcs12 -export -in fullchain.pem -inkey privkey.pem -out keystore.p12 -name airpageserver -CAfile chain.pem -caname root
> password: 123456
> verify password: 123456
```



#### keystore.p12 백앤드 폴더로 이동 

```
$ sudo cp /etc/letsencrypt/live/`server_name`/keystore.p12 /var/lib/jenkins/workspace/sucheol's/backend
```



#### application.properties 환경설정 추가

/backend/src/main/resources/application.properties

```
#ssl

server.ssl.key-store=keystore.p12
server.ssl.key-store-type=PKCS12
server.ssl.key-store-password=123456
server.ssl.key.alias=spring

#필요시 사용
#server.port=8443
#server.port.http=8080
```





# Jenkins

## 젠킨스란?

젠킨스는 소프트웨어 개발 시 지속적으로 통합 서비스를 제공하는 툴이다. CI(Continuous Integration) 툴 이라고 표현한다.

다수의 개발자들이 하나의 프로그램을 개발할 때 버전 충돌을 방지하기 위해 각자 작업한 내용을 공유영역에 있는 저장소에 빈번히 업로드함으로써 지속적 통합이 가능하도록 해준다.

***

참고 URL: https://ict-nroo.tistory.com/31

***





## Jenkins 설치

java, nginx(웹서버) 설치 필요



```
$ wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
```



```
$ sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```



```
$ sudo apt update

$ sudo apt install jenkins
```



>sudo ufw allow 8080



## Jenkins 접속하기 

http://your_ip_or_domain:8080 # 설정한 포트번호로 접속하기

Administrator password : `initialAdminPassword`

```
$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword
> 66d1df7616f641acac5a82cf54112a0d
```



### Customize Jenkins

**Install suggested plugins** vs select pulgins to install

추후 플러그인 설치 가능 

 

### Create First Admin User 

```
Username: 

Password: 

Confirm password: 

Full name: 

E-mail address:
```

 

### port for HTTP connector (default 8080; disable with -1)

- 톰캣의 기본 포트번호 8080사용할 경우 에러 



#### Jenkins port 번호 변경

```
$ sudo vi /etc/default/jenkins
> HTTP_PORT=8080 #=> 원하는 포트 번호로 변경
```

#### 

```
$ sudo service jenkins restart
```





***

참고 URL : https://medium.com/@donggyu9410/ubuntu%EC%97%90%EC%84%9C-jenkins-8080%ED%8F%AC%ED%8A%B8%EA%B0%80-%EC%95%84%EB%8B%8C-%EB%8B%A4%EB%A5%B8-%ED%8F%AC%ED%8A%B8%EC%97%90%EC%84%9C-%EC%8B%A4%ED%96%89%EC%8B%9C%ED%82%A4%EA%B8%B0-b083b4991ac1

***



***

참고 URL : https://linuxize.com/post/how-to-install-jenkins-on-ubuntu-18-04/

***







### 플러그인 설치

- Jenkins 관리 > System Configuration > 플러그인 관리 > 설치 가능

**Gitlab 설치**





### Global Tool Configuration

- Jenkins 관리 > System Configuration > Global Tool Configuration

**JDK**

```
Name jdk8
JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64
```



**Maven**

```
Name mvn
MAVEN_HOME /usr/share/maven
```



### Credentials

#### 1. Token

[Jenkins]

- Jenkins 관리 > Security >Manage Credentials > global > Add Credentials 

```
Kind `GitLab API token`
Scope `Global`
API token `Your New Personal Access Token`
ID `test`
Description 
```



[GitLab]

- gitlab Setting > Access Tokens > Personal Access Tokens

```
Name `jenkins-token`
Expires at `2020-12-31`
scope api
```

##### Your New Personal Access Token : `fgQYP9xhesSS1nfAAVCU`



#### 2. ID/PW

[Jenkins]

```
Kind `Username with password`
Scope `Global`
Username `jy5031le@gmail.com`
Password `password`
ID `test`
Description
```



### 시스템 설정

- Jenkins 관리 > System Configuration > 시스템 설정

홈 디렉터리  `/var/lib/jenkins`

Jenkins Location `3.35.111.185:9090/`



#### **Gitlab**

```
Connection name `gitlab-test`

Gitlab host URL `https://lab.ssafy.com/`

Credentials `GitLab API token`

# Test Connection Success
```



## Jenkins Item

**an item name** `jenkins-test`

**Freestyle project**



### :small_orange_diamond: General

GitLab Connection `gitlab-test` 



### :small_orange_diamond: 소스 코드 관리

Repositories

```
Repository URL `https://lab.ssafy.com/s03-final/s03p31b107.git`
Credentials `jy5031le@gmail.com/******
```



### :small_orange_diamond: 빌드 유발

```
✅ Build when a change is pushed to GitLab. GitLab webhook URL: http://3.35.111.185:9090/project/jenkins-test
> 고급...

Secret token Generatre
> ecb4d671e0125a3b9a9db0a6f303f834

```



[GitLab]

- project > Setting > Integrations(Maintainer 권한) 



**Integrations** 

```
URL `http://3.35.111.185:9090/project/jenkins-test`
Secret Token `ecb4d671e0125a3b9a9db0a6f303f834`
> Add Webhook
> Test Push Events
> Hook executed successfully: HTTP 200
```



Jenkins > jenkins-test(item) > 작업공간



##### ![img](http://3.35.111.185:9090/static/e80f5dce/images/48x48/error.png)에러: 작업공간이 없습니다.

A project won't have any workspace until at least one build is performed.

```
Build Now
> /var/lib/jenkins/workspace/jenkins-test
```

/var/lib/jenkins/workspace/jenkins-test 하위에 깃 파일이 생성



### :small_orange_diamond: ​Build 

- Add build step > Execute shell

```
echo "> frontend start !!!"
cd frontend
npm i
npm run build
```



- Add build step > Execute shell

```
echo "> backend start !!!"
pwd
cd backend
./temp.sh
sudo mvn spring-boot:run &
```



#### temp.sh (현재 실행중인 백서버 종료 후 실행)

```
echo "> Check the currently running spring server pid "
 CURRENT_PID=$(ps -ef | grep java | grep tomcat | awk '{print $2}')
echo "$CURRENT_PID"
 if [ -z $CURRENT_PID ]; then
echo "> No applications are currently running and will not be shut down."
else
echo "> kill -9 $CURRENT_PID"
sudo kill -9 $CURRENT_PID
fi
```

#### sudo mvn spring-boot:run & error => permission denied error 뜨면 
```
$ cd /var/lib/jenkins/workspace/jenkins-test/backend
$ sudo chmod 755 mvn

또는 실행권한 +
```

