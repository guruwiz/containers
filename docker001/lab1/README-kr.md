# hello earth 
 또 다른 hello world 유형 고정 컨테이너 예제 

 이 예제는이 실습 랩에 사용되며 호스트 포트 80에서 실행됩니다 

 이 예제를 GitHub 계정으로 포크 한 다음 Docker 허브 계정에 빌드 한 후 아래의 Docker 명령에서 &quot;username&quot;을 Docker 허브 사용자 이름으로 바꿉니다. 

 이 이미지를 가져 오려면 다음을 수행하십시오. 
```
docker pull username/hello-earth:latest
```

 이 이미지를 실행하려면 다음을 수행하십시오. 
```
docker run -d -p 80:80/tcp "username/hello-earth:latest"
```
