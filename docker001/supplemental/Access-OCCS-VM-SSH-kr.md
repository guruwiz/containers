#이 지침에 따라 SSH를 통해 컨테이너 클라우드 서비스 도커 VM에 액세스하십시오. 

 이 실습을 위해 Oracle Container Cloud Service (OCCS) 인스턴스를 사용하는 경우 사전 설치된 Docker Engine과 함께 사전 구축 된 Oracle Linux VM (Worker 노드라고도 함)을 활용할 수 있습니다. 

 **이 방법을 사용하는 경우이 HOL을위한 사전 작업의 일부로 OCCS 인스턴스를 이미 제공 했어야합니다. ** 

 첫 번째 단계는 OCCS &quot;작업자 노드&quot;또는 Docker 호스트 중 하나에 SSH를 연결하고 Docker 설치를 확인하고 버전을 확인하는 것입니다. 작업자 노드는 단순히 Docker 컨테이너를 실행할 수있는 Docker Host / VM입니다. 

 OCCS 인스턴스를 만들 때 사용한 SSH 키를 사용하여 Pre-built ContainerCS 인스턴스의 작업자 노드에 첫 번째 SSH를 만듭니다. 

 Worker Node IP 주소를 찾으려면 Oracle Cloud My Services Portal에 로그인하고 Container Cloud Service Console의 Worker Node에서 공용 IP 중 하나를 사용하십시오. 

<img src=../images/003-worker-ip.png />


 Worker 노드 IP와 개인 키의 경로로 아래 명령을 수정하십시오. 

```
$ ssh opc@ip_address -i /users/yourName/folder/sshkey/privateKey
```

> *Note - the above format is usable directly in a Mac terminal. If you are using a Windows computer, use an appropriate Windows SSH client, like Putty or another SSH client*
