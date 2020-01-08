처음은 미비하지만 꾸준함을 토대로 문을 두드리기 위함 첫 시작

KAFKA 시작 



KAFKA 설치

0. 설치 환경

   0.1) virtual box
   0.2) centos7
   0.3) Docker version 19.03.5
   0.4) docker-compose version 1.22.0

1. 일반 패키지 다운로드 후 저장 및 설치

2. docker를 이용한 설치
   
   root로 실행
   
   # docker 설치
   yum install -y yum-utils device-mapper-persistent-data lvm2
   yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
   yum install docker-ce -y
   
   # docker-compose 설치
   curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o 
   /usr/local/bin/docker-compose
   chmod +x /usr/local/bin/docker-compose

   # docker 실행
   systemctl start docker

3. kafka-manager 설치 

   카프카 설치 후 운영 및 모니터링이 CLI에 국한되어 실제 쉽지 않은 상황 
   그와중에 검색을 토대로 하둡 관련 ambari 같은 관리 웹 서비스가 있음을 발견후 
   설치 및 적용 결심 
   
   wget https://github.com/yahoo/kafka-manager/archive/1.3.3.22.tar.gz
   tar -zxvf 1.3.3.22.tar.gz
   cd kafka-manager-1.3.3.22

도움 주신 곳 - 정말 감사합니다. 
도커로 설치 관련 
https://m.blog.naver.com/PostView.nhn?blogId=occidere&logNo=221390946271&proxyReferer=https%3A%2F%2Fwww.google.com%2F
카프카 전반적인 설치 내용 
https://github.com/itmare/kafka/tree/master/practice

