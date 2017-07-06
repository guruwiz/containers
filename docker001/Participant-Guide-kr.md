# 용기 소개 

 이 Hands on Lab (Hands on Lab)은 참가자들에게 컨테이너 화의 기초를 배우고 그 장점을 탐색하며 초보 수준의 연습으로 Docker 기술을 소개합니다. 이 2 시간 세션에서 다룰 주제는 다음과 같습니다. 

 1. [기본 컨테이너 개념 소개] (Participant-Guide.md # 기본 컨테이너 개념 소개) 
 2. [실험실 환경에서 Docker Engine이 작동하는지 확인] (Participant-Guide.md # verify-docker-engine-hands-on-lab-environment) 
 3. [안녕하세요 헬로우 월드] (참여자 - 가이드 .md # hello-helloworld) 
 5. [Dockerfile 및 도커 이미지 만들기] (Participant-Guide.md # dockerfile 및 docker 이미지 만들기) 
 6. [도커 허브 계정으로 이미지 푸쉬] (Participant-Guide.md # 도커 허브 계정 푸시 - 이미지) 
 7. [Docker Compose 설치] (Participant-Guide.md # install-docker-compose) 
 8. [Wordpress &quot;스택&quot;만들기] (Participant-Guide.md # create-a-wordpress-stack) 
 9. [영구 저장소의 기본 사항] (Participant-Guide.md # 영구 저장소의 기본 사항) 
 10. [Github와 Docker Hub를 함께 사용하여 이미지를 만들고 컨테이너를 실행하십시오] (Participant-Guide.md # github-and-docker-hub-a-image-and-run-the-image -컨테이너) 
 11. [참가자의 컨테이너를 보여주는 Oracle Container Cloud Service 데모] (Participant-Guide.md # 데모 오브 오라클 컨테이너 클라우드 서비스 표시 참가자 컨테이너) 


 ###이 HOL을 완료하기위한 요구 사항 : 

 사전 구성된 Docker-Engine 환경 - [필수 구성 요소] (Prerequisites.md)를 참조하십시오. 

 * 인터넷 접속 

 * 노트북 

 * 메모 및 스 니펫을 계속 유지하는 텍스트 편집기 

 * Docker 허브 계정 

 * Github 계정 

 *** 

 ## 기본 컨테이너 개념 소개 

 컨테이너는 Docker 이미지의 런타임 인스턴스입니다. 

 [https://docs.docker.com/engine/reference/glossary/#/container](https://docs.docker.com/engine/reference/glossary/#/container) 

 Docker는 회사 및 컨테이너 화 기술입니다. 

 [https://docs.docker.com/engine/reference/glossary/#/docker](https://docs.docker.com/engine/reference/glossary/#/docker) 

 컨테이너는 오랫동안 사용되어 왔습니다. Docker는 단순한 인간이 사용할 수있는 기술을 개발했으며 이전보다 훨씬 쉽게 이해할 수있었습니다. 따라서 ** 휴대용 및 경량 응용 프로그램 패키징 기술을 개발하는 데 엄청난 지원을 얻었습니다. ** 

 그러나 컨테이너 기술의 변형이 여전히 존재합니다. 몇 년 동안 우리가 본 몇 가지 기술이 있습니다. 

 리눅스 컨테이너의 역사 : 

<img src=images/002-container-history.png />


 이제 가상 머신 (VM)이 컨테이너와 어떻게 다른지 살펴 보겠습니다. 

 컨테이너는 VM처럼 들릴 수 있지만 두 기술은 서로 다른 기술입니다. VM을 사용하면 각 가상 시스템에 응용 프로그램, 필요한 바이너리 및 라이브러리 및 전체 게스트 운영 체제가 포함됩니다. ** 

 반면에 컨테이너는 응용 프로그램과 모든 종속성을 포함하지만 커널을 다른 컨테이너와 공유하며 호스트에 Docker 엔진을 설치하는 것 이외의 특정 인프라에 묶이지 않습니다. 거의 모든 컴퓨터, 인프라 및 시스템에서 컨테이너를 실행할 수 있습니다. 구름. 

<img src=images/002-vm-vs-container.png />


> *Note - at this time, Windows and Linux containers require that they run on their respective kernel base, therefore, Windows containers cannot run on Linux hosts and vice versa.*

 Docker 이미지는 컨테이너 내부에서 소프트웨어 응용 프로그램을 실행하는 데 필요한 모든 것을 가진 파일 모음입니다. 그러나 컨테이너가 실행되는 동안 컨테이너 내부에 작성된 모든 데이터는 유지되지 않습니다. 

 컨테이너가 이미지에서 중지되었다가 다시 시작되면 컨테이너는 마지막 실행주기 동안 변경된 내용이없는 처음과 완전히 동일하게 실행됩니다. 컨테이너의 변경 사항은 이미지 작성 프로세스 중에 이미지의 일부가되는 Dockerfile을 사용하여 작성하거나 컨테이너 내부에서 외부로 영구 저장 볼륨을 마운트하여 데이터를 유지할 수 있습니다. 이것은 아래의 HOL 연습에서 더 자세히 살펴볼 것입니다. 

<img src=images/004-docker-images.jpg />


 약간 뒤로 돌아가서 Docker가 소개하는 새로운 명명법이 있습니다. 여기에 익숙해 져야 할 용어가 있습니다. 

 이 Docker 기술 각각은이 HOL에서 탐구 될 것입니다. 이 핵심 기술은 오픈 소스라는 점에 유의해야합니다. 더 큰 생태계에는 유료 지원 옵션이있는 오픈 소스, 라이센스 또는 하이브리드 일 수있는 다른 기술이 있습니다. 

<img src=images/005-docker-terms.jpg />


 Docker 엔진은 컨테이너를 실행할 수있는 핵심 기술입니다. 최소한 Linux 컨테이너에서 컨테이너를 실행하려면 Docker Engine을 설치해야합니다. 그런 다음 Docker Engine이 설치된 모든 Linux 호스트에서 컨테이너를 실행할 수 있으므로 각 호스트에서 응용 프로그램 별 구성 변경 없이도 이식성의 이점을 얻을 수 있습니다. 

<img src=images/004-docker-engine.jpg />


 좋습니다, 그것들은 기술의 메카니즘 중 일부입니다 만, Docker가 모든 유형의 IT 사람들에게 인기가있는 이유는 무엇입니까? Developers 및 IT Ops의 이러한 증명 포인트를 살펴 보겠습니다. 

<img src=images/004-why-containers.jpg />


 또한 Docker를 탐색하고 사용하는 수백 개의 조직과 이야기 할 때 Docker가 제공하는 핵심 이점이 있습니다. 

<img src=images/005-docker-usage.jpg />


 이 모든 것은 여러 가지 측면에서 기술 혁신의 일부이며 현대 민첩한 애플리케이션 개발의 기초입니다. 

<img src=images/006-evolution.jpg />

 *** 

 ## 랩 환경에서 Docker Engine이 작동하는지 확인 

 이 첫 번째 섹션에서는 [필수 구성 요소 문서] (Prerequisites.md)에서 요청한대로 Docker 엔진 환경에 연결할 수 있는지 확인합니다. 지금 환경에 액세스하여 터미널에서 다음 명령을 실행하십시오. 

> *Note - if you are using one of the Worker Nodes in an Oracle Container Cloud Service instance, as your Docker Engine environment, [access it via SSH per these instructions](supplemental/Access-OCCS-VM-SSH.md)

 ** 선택 사항 ** - 편의상 root로 실행하므로 sudo로 모든 것을 시작하지 않아도됩니다 (Windows 용 Docker를 실행하는 경우에는 적용되지 않음). 

```
$ sudo -s
```

 다음은 설치된 버전을 확인하는 Docker 전용 명령입니다. 

```
$ docker --version
```

 Docker가 설치되어 실행 중이면 다음과 같은 출력이 표시됩니다. 

```
Docker version 1.1x.x, build 57bf6fd
```

 *** 

 ## Hello Helloworld 

 Docker의 Hello world 예제를 실행합니다. 


```
$ docker run hello-world
```

 &quot;hello-world&quot;이미지는 호스트에서 로컬로 사용할 수 없으므로 명령은 공용 Docker 허브 이미지 저장소에서 hello-world 이미지를 자동으로 가져 와서 포 그라운드에서 컨테이너를 실행합니다. 

<img src=images/2017-03-16_13-40-42.jpg />

 *** 

**Congratulations, you have just run your first Docker container!**

 모든 용기를 나열하십시오 : 

> *Note - the "- a" option = running **and** stopped*

```
$ docker ps -a
```
hello-world 컨테이너가 한 번 실행 된 다음 종료되었습니다. 

<img src=images/2017-03-16_14-46-49.jpg />

 *** 

 이 연습에서는 Docker Hub에서 다른 Docker 이미지를 탐색합니다. 

 ** Docker Hub에서 공개 이미지 Helloworld 예제를 찾아보십시오. 그것을 실행하십시오. ** 

 이 Docker 허브 이미지 사용 : 

 [https://hub.docker.com/r/karthequian/helloworld](https://hub.docker.com/r/karthequian/helloworld) 

 Docker Hub Registry에서 이미지를 당겨 : 

>  *Note - observe how the layers are pulled individually.  Docker image files are composed of multiple layers, for more information, read the [Docker docs here about images and layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/)*

```
$ docker pull karthequian/helloworld:latest
```

 Docker Hub 페이지에서 Docker Run 명령을 복사 / 붙여 넣기하고 &quot;-d&quot;옵션을 추가하여 컨테이너가 &quot;detached&quot;모드로 실행되도록하십시오 : 

> *Note - the "-d" option run the container in detached mode, as opposed to the foreground mode that you saw in the last exercise.  The benefit of this is that for longer running containers, it frees up your terminal window.*

```
$ docker run -d -p 80:80/tcp "karthequian/helloworld:latest"
```

 브라우저에서 Helloworld 앱을 탐색하십시오. 실행중인 Docker Host의 IP로 이동하여 방문수를 기록하십시오. 

> *Note - the IP is the same as the Host that you are SSH’d into http://host_ip or on your localhost http://localhost (for the rest of this document, it may just be referred to as host IP or Docker host IP for simplicity)*


<img src=images/004-hello-world.png />

 *** 

 이제 Docker 컨테이너에있는 응용 프로그램을 실제로 사용하고 있습니다. 브라우저를 새로 고침하고 방문수가 어떻게 증가하는지 관찰합니다. 이것은 실제 응용 프로그램입니다. 간단한 예제이지만 컨테이너에서 실행중인 응용 프로그램 사용 경험의 예입니다. 컨테이너에서 실행되지 않는 경우와 다를 바 없습니다. 

> *Makes you wonder about how many apps that you are using on a day to day basis, may indeed be running in a Docker container?*

 이제 Docker가 실행중인 Helloworld 컨테이너를 할당 한 이름을 살펴보십시오. 

 실행중인 모든 컨테이너 나열 : 

```
$ docker ps
```

 Docker가 아래에 &quot;ecstatic_lamport&quot;와 같은 컨테이너 이름을 지정했는지 확인하십시오. Docker가 컨테이너에 어떤 이름을 지었습니까? 이 이름을 기억해 두십시오. 조금만 사용하겠습니다. 

<img src=images/2017-03-16_13-49-25.jpg />

 *** 

> *Note - unless you specify a container name, Docker will assign a similar 2 part name automatically*

 ** 더 구체적인 이름으로 컨테이너를 중지하고 다시 실행하십시오 ** 

 이제 터미널 창으로 돌아가서 컨테이너를 멈추고 더 많은 설명이 포함 된 이름을 지정하면 실행중인 컨테이너가 많은 경우 더 쉽게 찾을 수 있습니다. 

 실행중인 컨테이너 중지 - 아래 ** your_container **를 실행중인 컨테이너의 실제 이름으로 바꿉니다. 

```
$ docker stop your_container
```

 이제 &quot;rm&quot;명령을 사용하여 컨테이너를 제거하십시오. 

```
$ docker rm your_container
```

 컨테이너가 제거되었는지 확인하십시오. 

```
$ docker ps -a
```

> *Note - containers can be stopped and removed by using their name **(if there are no dependent image layers)**, their long id or their short id*

 이제 &quot;helloworld_app&quot;와 같이 더 알기 쉬운 이름으로 컨테이너를 실행하십시오. 

```
$ docker run -d --name helloworld_app -p 80:80/tcp "karthequian/helloworld:latest"
```

 실행중인 모든 컨테이너를 다시 나열하십시오. 

```
$ docker ps
```

> *Is the container easier to find now, especially that there is context to the name of the container?  Especially if there were many containers running?*

 컨테이너를 중지하고 제거하십시오. 

```
$ docker stop helloworld_app

$ docker rm helloworld_app
```

 우리는 HOL의이 부분을 완성합니다. 

 *** 

 ## Dockerfile 및 Docker 이미지 만들기 

 이 연습에서는 Dockerfile에서 자신의 이미지를 빌드합니다. 

 ** DockerFiles 정보 ** 

 Dockerfile은 기본 이미지 (일반적으로 Alpine Linux와 같은 씬 Linux OS 배포판)로 시작한 다음 응용 프로그램 및 구성에 레이어를 작성하는 방법입니다. [Docker에 따르면] (https://docs.docker.com/engine/reference/builder/) : 

 * &quot;Dockerfile은 사용자가 이미지를 어셈블하기 위해 명령 줄에서 호출 할 수있는 모든 명령을 포함하는 텍스트 문서입니다 .Docker 빌드 사용자는 여러 명령 줄 명령을 연속적으로 실행하는 자동화 된 빌드를 만들 수 있습니다.&quot;* 

 ** 도커 이미지 만들기 ** 

 [Docker Whalesay] (https://hub.docker.com/r/docker/whalesay/) 예제를 사용하여 첫 번째 이미지를 만듭니다. 

 다음 단계를 따르십시오. 

 홈 디렉토리에서 Dockerfile을 저장할 디렉토리를 만듭니다. 

```
$ cd ~ 

$ mkdir mydockerbuild
```

 새 디렉토리로 변경하십시오. 

```
$ cd mydockerbuild
```

 1.3 단계에서 VI 또는 nano와 같이 선택한 편집기를 사용하십시오. 

 Oracle Linux를 사용하는 경우 VI를 사용하십시오. 

> *Note - case is important in the file name "Dockerfile".  Use a capital D and lower case for the rest of the letters.*

```
$ vi Dockerfile
```

 다음 세 줄의 Dockerfile이라는 텍스트 파일을 만듭니다. 

> *Note - if you are using VI, press the "i" key first to enter insert mode, before you paste.

```
FROM docker/whalesay:latest

RUN apt-get -y update && apt-get install -y fortunes

CMD /usr/games/fortune -a | cowsay
```

 1.8 단계에서 VI가있는 Dockerfile에 3 줄을 추가 한 후에는 Esc 키 - 콜론 -w (쓰기) - q (종료)를 입력하여 파일을 저장하십시오. 


```
esc : w q 
```

 Dockerfile의 내용이 올바른지 확인하십시오. 

```
$ cat Dockerfile
```

> *Note - the docs for VI are here: [https://www.cs.colostate.edu/helpdocs/vi.html](https://www.cs.colostate.edu/helpdocs/vi.html)*

 그런 다음 섹션 2에서 Docker 이미지를 작성하고 &quot;.&quot; 명령의 끝에서 : 

```
$ docker build -t docker-whale .
```

 그런 다음 섹션 4에서 호스트의 이미지를 나열하고 도커 - 고래 이미지를 컨테이너로 실행하십시오. 

```
$ docker images
```

```
$ docker run docker-whale
```

 터미널에서 출력을 확인하면 컨테이너가 한 번 실행 된 다음 중지됩니다. 

<img src=images/2017-03-16_14-10-47.jpg /> 

 *** 

 ## 이미지를 도커 허브 계정에 푸시 

 ** 레지스트리 ** 

 레지스트리는 Docker 이미지를 저장합니다. Docker를 노트북에서 떼어내는 첫 번째 단계는 레지스트리를 사용하는 것입니다. 가장 널리 사용되는 레지스트리는 Docker Hub입니다 : [https://hub.docker.com] (https://hub.docker.com) 

> *Note - in this exercise you will need a Docker Hub account to use the public Docker registry.  If you do not have one already, you can sign up for free, navigate to: [https://hub.docker.com/](https://hub.docker.com/)*

 ** 태그를 달고 새 이미지를 Docker 허브 레지스트리에 푸시하십시오. 이 연습에서 사용자 이름은 Docker 허브 계정 이름입니다. ** 

 먼저 터미널에서 Docker 허브 계정에 로그인하십시오. 

```
$ docker login
```

 메시지가 나타나면 Docker 계정 사용자 이름 (소문자), 비밀번호 및 이메일을 입력하십시오. 

 이제 Docker Hub에서 새 docker-whale 이미지에 태그를 달고 계정에 푸시하십시오. 

 Docker ** 사용자 이름 **을 다음으로 대체하십시오. 

```
$ docker tag docker-whale:latest username/docker-whale:latest
```

 Docker 이미지를 계정으로 푸시합니다. 그러면이 이미지에 대해 &quot;docker-whale&quot;이라는 새 저장소가 만들어집니다. 

```
$ docker push username/docker-whale:latest
```

 Docker 허브의 계정 페이지로 이동하여 ** 사용자 이름 **을 대체하십시오. 

 [https : //hub/docker.com/r/username] (https://hub.docker.com/r/username) 

 당신이 밀어 넣은 이미지가 보이나요? 

<img src=images/010-docker-hub.png />

 *** 

 이제 로컬 이미지를 제거하고 Docker Hub 레지스트리에서 이미지를 가져 와서 실행하십시오. 

 이렇게하려면 중지 된 컨테이너를 이름이 아닌 짧은 ID를 사용하여 먼저 제거해야합니다. 짧은 ID 찾기 : 

```
$ docker ps -a 
```

 해당 컨테이너의 짧은 ID를 복사하면 ee31fe1dd8f8 형식과 유사하게되며 &quot;rm&quot;명령을 사용하여 컨테이너를 제거하십시오. 

```
$ docker rm short_id
```

 컨테이너가 제거되었으므로 이미지를 호스트에서 로컬로 제거하고 Docker 허브의 이미지에서 컨테이너를 강제로 실행할 수 있습니다. &quot;rmi&quot;명령을 사용하여 이미지를 제거하십시오. 

 Docker 허브에 푸시 한 이미지를 로컬에서 제거하십시오. 

```
$ docker rmi username/docker-whale
```

 이미지가 호스트에서 제거되었는지 확인하십시오. images 명령을 사용하여 모든 Docker 이미지를 봅니다. 

```
$ docker images
```

 이제 Docker Hub의 저장소에서 이미지를 직접 실행하고 이미지가 로컬에 존재하지 않기 때문에 이미지를 새로 끌어 오십시오. 

```
$ docker run username/docker-whale
```

> *Note - if no tag is used, the default tag is "latest", and it is pulled from your registry*

<img src=images/2017-03-16_14-17-38-2.jpg />

 *** 

 **이 시점에서 모든 용기를 중지하고 제거하십시오. 모든 컨테이너에서이 작업을 수행하려면 다음 명령을 사용하십시오. ** 

```
$ docker stop $(docker ps -a -q)

$ docker rm $(docker ps -a -q)
```

 *** 

 ## Docker 설치하기 Compose 


 ** Docker 소개 Compose ** 

 Docker Compose 란 무엇입니까? 왜 사용합니까? 

 Docker에 따르면 * Docker Compose는 다중 컨테이너 Docker 응용 프로그램을 정의하고 실행하기위한 도구입니다. 작성을 사용하면 작성 파일을 사용하여 응용 프로그램의 서비스를 구성 할 수 있습니다. 그런 다음 단일 명령을 사용하여 구성에서 모든 서비스를 만들고 시작하십시오. * 

 ** Docker Compose 설치 ** 

> *For simplicity, you will install Docker Compose v1.12 in a directory called "compose", under the root home directory to avoid any path issues with the variety of Linux environments that may be used in this HOL.  This is also where you will run Docker Compose locally in that directory and create your first docker-compose.yml file.*

 루트 홈 디렉토리로 변경하십시오. 

```
$ cd ~
```

 루트 홈 디렉토리에 있는지 확인하십시오. 

```
$ pwd
```

 &quot;compose&quot;라는 새 디렉토리를 만듭니다. 

```
$ mkdir compose
```

 이 새 디렉토리로 변경하십시오. 

```
$ cd compose
```

 그런 다음이 curl 명령을 사용하여 해당 디렉토리에 Docker Compose v1.12를 로컬로 설치하십시오. 

```
$ curl -L "https://github.com/docker/compose/releases/download/1.12.0/docker-compose-$(uname -s)-$(uname -m)" -o docker-compose
```

 실행 권한을 변경하십시오. 

```
$ chmod +x docker-compose
```

 설치된 Docker Compose 버전을 확인하고 확인하십시오. 

```
$ ./docker-compose --version
```

> *Note - for further information, please refer to these Docker docs at a later time: [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)*
*** 

 ## Wordpress &quot;스택&quot;만들기 

 간단한 Wordpress 스택을 만들려면 다음 단계를 따르십시오. 

 편집기 또는 VI를 사용하여 &quot;docker-compose.yml&quot;파일을 생성하십시오 : 

> *Note - just as with the Dockerfile above, case of the file name is important.  Use all lower case for "docker-compose.yml"*

```
$ vi docker-compose.yml
```

 다음 텍스트 또는 YAML을 복사하여 붙여 넣으십시오. 

```
version: '2'

services:
   db:
     image: mysql:5.7
     volumes:
       - db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: wordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "80:80"
     restart: always
     volumes:
       - /var/www/html:/var/www/html:rw
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_PASSWORD: wordpress
volumes:
     db_data:
```


 docker-compose.yml을 저장하십시오. 

 VI를 사용한다면 Esc 키 - 콜론 - w (쓰기) - q (종료)를 입력하여 파일을 저장하십시오 : 


```
esc : w q 
```

 docker-compose.yml 파일의 내용이 올바른지 확인하십시오. 

```
$ cat docker-compose.yml
```

 이 명령으로 Wordpress 스택을 실행하십시오 : 

```
$ ./docker-compose up -d
```

 ** Wordpress 설정 페이지를 방문하여 실행중인 스택을 확인하십시오. ** 

 브라우저에서 호스트 IP를 사용하여 아래 URL을 복사하여 Wordpress 설정을 시작하십시오. 

```
http://host_ip/wp-admin/install.php
```

> *Note - Docker for Mac users - if the following error is observed, try restarting the Docker service on the Mac, to allow writes to /var/www/html*

```
ERROR: for wordpress  Cannot start service wordpress: Mounts denied: 
The path /var/www/html
is not shared from OS X and is not known to Docker.
You can configure shared paths from Docker -> Preferences... -> File Sharing.
```

**Congratulations, you have successfully launched your first Wordpress app in Docker!**
```
     volumes:
       - /var/www/html:/var/www/html:rw
```

 데이터베이스에 대한이 볼륨 문. 이 예에서 &quot;db_data&quot;가 호스트 볼륨에 저장된 위치를 Docker가 매핑하도록합니다. 

```
     volumes:
       - db_data:/var/lib/mysql
 ```

 호스트 볼륨이 먼저 나열된 다음 컨테이너 볼륨이 콜론으로 구분됩니다. 이는 지정된 컨테이너 볼륨 경로에 기록 된 모든 데이터를 호스트 볼륨에 바인드합니다. 컨테이너가 중지되고 동일한 호스트에서 다시 실행되면 호스트 볼륨에서 기존 데이터를 가져옵니다. 

 * 이제 우리가 탐구 할 마법을 알게되었습니다. * 

 ** Wordpress 설정을 완료하고 블로그 게시물을 만드십시오. ** 

 브라우저에서 Host_IP로 이동하여 다음과 같이 Wordpress 초기화 URL : /wp-admin/install.php와 함께 추가하십시오. 

> *Note - this is the same setup URL you saw when you deployed with Docker Compose above.  You may already have this loaded in a browser tab.*


```
http://docker_host_ip/wp-admin/install.php
```

 먼저 언어를 선택하십시오. 

<img src=images/033-wp-setup1.png />

 *** 

 Wordpress 로그인 정보를 설정하십시오. 노트에 사용자 이름과 비밀번호를 보관하십시오. 

<img src=images/034-wp-setup2.png />

 *** 

 Wordpress에 로그인하려면 &quot;로그인&quot;버튼을 클릭하십시오 : 

<img src=images/034-wp-setup2.png />

 *** 

 이전에 생성 한 자격 증명을 사용하여 로그인하십시오. 

<img src=images/036-wp-login2.png />

 *** 

 다음 단계 섹션에서 &quot;첫 번째 블로그 게시물 작성&quot;을 선택하십시오. 

<img src=images/037-write-blog.png />

 *** 

 샘플 블로그 게시물을 만드십시오. 원하는 경우 이미지를 포함하고 게시를 클릭하십시오. 

<img src=images/038-publish-blog.png />

 *** 

 블로그 게시물로 이동하려면 &quot;Permalink&quot;를 클릭하십시오 : 

<img src=images/039-permalink.png />

 *** 

 블로그 게시물의 퍼머 링크 URL을 복사하여 나중에 필요할 때 메모에 보관하십시오. 

<img src=images/040-view-blog.png />

 *** 

 실행중인 Wordpress 및 Database 컨테이너를 짧은 ID로 중지하고 제거하십시오. 

 이전 실습에서이 점을 기억하십시오. 

```
$ docker ps -a

$ docker stop short_id

$ docker rm short_id
```

 모든 컨테이너가 중지되고 제거 될 때까지 다음 컨테이너에 대해 반복하거나 이전에 표시된 대량 제거를 사용하십시오. 


 페이지를 새로 고침하여 Wordpress 블로그 게시물이 사라 졌는지 브라우저에서 확인하십시오. 

<img src=images/043-refresh.png />

 *** 

 Wordpress 스택 재배포 : 

```
$ ./docker-compose up -d
```

 브라우저에서 기록한 블로그 게시물 URL로 돌아가서 페이지를 새로 고칩니다. 

<img src=images/047-refresh-blog.png />

 *** 

 데이터는 호스트 볼륨에 기록되고 동일한 호스트에 재배포 될 때 컨테이너에 다시 연결되기 때문에 지속됩니다. 


 ** 다음 섹션으로 이동하기 전에 모든 용기를 중지하고 제거하십시오 : ** 

```
$ docker stop $(docker ps -a -q)

$ docker rm $(docker ps -a -q)
```

 *** 


 ## GitHub와 Docker Hub를 함께 사용하여 이미지를 만들고 컨테이너를 실행하십시오. 

 ** 요구 사항 : GitHub 및 Docker 허브의 사용자 계정 ** 

> *Note - if you do not have a Github account, get a free one here: [https://github.com/join](https://github.com/join)* 

 이제 GitHub 및 Docker 허브를 사용하여 이미지를 만드는 또 다른 방법을 살펴 보겠습니다. 

> *Note - in this exercise you will fork an existing hello-world like repository, that you will call hello-earth, then modify its web page: Index.html in GitHub to trigger an automated Docker image build in Docker Hub.  You will then verify the successful build and run the image as a container in your Docker environment.*


 ** 시작하려면이 GitHub Docker001 레포를 자신의 포크로 포크하십시오 ** 

 로그인 GitHub 계정 : 

 https://github.com/login 

 브라우저에서 다음 GitHub 저장소로 이동합니다. 

 https://github.com/oracle/cloud-native-devops-workshop/tree/master/containers/docker001 


 특정 GitHub 저장소에 대해 &quot;포크&quot;버튼을 선택하십시오 : 

<img src=images/github-dockerhub_14.jpg />

 *** 

 그러면 자동으로이 저장소가 자신의 GitHub 계정에 복사되며 필요한 경우 GitHub 계정을 편집 할 수 있습니다. 

<img src=images/github-dockerhub_9.jpg />

 *** 

 이제 브라우저의 다른 탭에서 Docker 허브 계정에 로그인하십시오. 

 https://hub.docker.com/login 


 Docker Hub 계정에서 Create 아래의 Top Menu에서 &quot;Create Automated Build&quot;를 선택하십시오. 

<img src=images/github-dockerhub_13.jpg />

 *** 

 Docker 허브가 소스 코드를 가져올 수 있도록 GitHub 계정을 연결하라는 메시지가 표시됩니다. 

<img src=images/2017-03-16_10-41-09.jpg />

 *** 

 다음과 같이 GitHub를 선택하십시오. 

<img src=images/2017-03-16_10-41-14.jpg />

 *** 

 공개 및 비공개 리포지토리 모두 선택 : 

<img src=images/2017-03-16_10-41-23.jpg />

 *** 

 다시 말하지만 Docker 허브 계정에서 Create 아래의 Top Menu에서 &quot;Create Automated Build&quot;를 선택하십시오. 

<img src=images/github-dockerhub_13.jpg />

 *** 

 Create Auto-Build :를 선택하십시오. 

<img src=images/github-dockerhub_11-2.jpg />

 *** 

 &quot;cloud-native-devops-workshop&quot;저장소를 선택하십시오 : 

<img src=images/github-dockerhub-21.jpg />

 *** 

 저장소 이름을 &quot;hello-earth&quot;로 만들고 간단한 설명을 추가하고 저장을 누릅니다. 

> *Note - naming the repository will also result in the image name being "hello-earth", after you do the first build.*

<img src=images/github-dockerhub_10.jpg />

 *** 

 Build Settings 탭에서 Dockerfile Location에 대해 &quot;/ containers / docker001 / lab1&quot;을 입력하고 &quot;Save Changes&quot;버튼을 누릅니다. 

<img src=images/github-dockerhub-20.jpg />

 *** 

 GitHub 계정으로 돌아가서 위의 Docker001 repo를 분기 한 URL로 이동하여 &quot;lab1&quot;폴더를 엽니 다. 아래 URL에 GitHub 사용자 이름을 바꿉니다. 

 https://github.com/*username*/cloud-native-devops-workshop/tree/master/containers/docker001/lab1 

 GitHub 페이지에서 &quot;Index.html&quot;링크를 클릭하십시오 : 

<img src=images/2017-03-16_11-15-12.png />

 *** 

 이 Index.html을 수정하여 새로운 &quot;Hello Earth&quot;웹 페이지를 만들면 Docker 허브에 새로운 이미지 빌드가 자동으로 트리거됩니다. 그런 다음 결과 이미지를 컨테이너로 실행하여 변경 사항을 관찰합니다. 

 연필 아이콘을 통해 페이지를 수정하십시오. 

<img src=images/050-edit-index.png />

 *** 

 Line 12를 다음과 같이 변경하여 myName 및 myCity가 표시된 사용자 이름과 도시를 대체하십시오. 

<img src=images/2017-03-16_11-19-42.jpg />

 *** 

 아래로 스크롤하여 변경 사항 적용. 설명을 추가하고 &quot;Commit Changes (변경 사항 적용)&quot;버튼을 누릅니다. 

<img src=images/052-commit-index.png />

 *** 

 그러면 DockerHub에서 DockerHub의 새 자동화 빌드가 실행되고, Dockerfile은 빌드 프로세스의 일부로 Index.html의 새로운 변경 사항을 통합합니다. 상태는 &#39;빌드 세부 정보&#39;탭에 표시됩니다. 빌드 상태에 대한 업데이트를 보려면 브라우저를 새로 고침해야합니다. 

> *Note - if the automated build does not happen automatically, you can just use the "Trigger" button in the Docker Hub - Build Settings tab to manually start an image build.*

<img src=images/github-dockerhub_3.jpg />

 *** 

 Docker Hub에서 빌드를 완료하는 데 몇 분이 소요됩니다. 성공하면 Status 열에 Success가 표시됩니다. 

> *Note - you may need to refresh your browser tab to see the updated status.*

<img src=images/github-dockerhub_1.jpg />

 *** 

 빌드가 완료되면 Docker CLI 환경으로 돌아가서 새 컨테이너를 실행하십시오. 아래 명령에서 &quot;username&quot;의 Docker Hub 이름을 바꿉니다. 

```
$ docker run -d -p 80:80 "username/hello-earth"
```

Once the container is running, visit the docker host’s IP and observe your changes for a new hello-earth container that you just built and ran!

<img src=images/github-dockerhub_15.jpg />

 *** 

Tweet to the world that you have created your own Hello Earth containerized app! 

> *Note - remember to use your Docker Hub account name where it says "username" in the tweet.*

```
Check out my Hello Earth #Docker app that I just created in my #OracleCode HOL.  It's in my Docker Hub https://hub.docker.com/r/username/hello-earth
```

**Congratulations!**  You have successfully completed this Hands On Lab!
