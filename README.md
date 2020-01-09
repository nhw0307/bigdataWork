처음은 미비하지만 꾸준함을 토대로 문을 두드리기 위함 첫 시작

KAFKA 시작 
==========

KAFKA 설치
----------

### 1. 설치 환경

    1. virtual box
    2. centos7
    3. Docker version 19.03.5
    4. docker-compose version 1.22.0
    5. JDK, wget 설치
   
     yum -y install java-1.8.0-openjdk
     yum -y install java-1.8.0-openjdk-devel
         java-1.8.0-openjdk-devel 
         이게 설치가 안되서 카프카 매니저 설치시에 ./sbt clean dist 이명령어로 ZIP 를 만들지 못하는 오류생김
     yum -y install####  #### wg
      
      
### 2. 일반 패키지 다운로#### 드 후 저장 및 설치


### 3. docker를 이용한 zookeeper kafka 설치
   
   root로 실행
   
   #### * docker 설치
      yum install -y yum-utils device-mapper-persistent-data lvm2
      yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
      yum install docker-ce -y
   
   #### * docker-compose 설치
   curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o 
   /usr/local/bin/docker-compose
   chmod +x /usr/local/bin/docker-compose

   #### * docker 실행
   systemctl start docker

 ### 4. kafka-manager 설치 

   카프카 설치 후 운영 및 모니터링이 CLI에 국한되어 실제 쉽지 않은 상황 
   그와중에 검색을 토대로 하둡 관련 ambari 같은 관리 웹 서비스가 있음을 발견후 
   설치 및 적용 결심 
   
   설치 장소 
   https://github.com/yahoo/kafka-manager/releases
   
   #### kafka-manager 설치 명령어 
   wget https://github.com/yahoo/kafka-manager/archive/2.0.0.2.tar.gz
   tar -zxvf /2.0.0.2.tar.gz
   cd kafka-manager-2.0.0.2
   
   #### sbt로 빌드 작업 
   ./sbt clean dist
   
   #### 빌드 후 ZIP 생성
    ~ target/universal/아래에 zip파일 생성
    
   #### 적당한 장소에 unzip하고 연결
    yum install unzip
    unzip -d ~/apps/ target/universal/kafka-manager-2.0.0.2.zip
    ln -s kafka-manager-2.0.0.2/ kafka-manager
    
   #### conf/application.conf에서 kafka-manager.zkhosts 수정
    vi conf/application.conf
    kafka-manager.zkhosts=주키퍼아이피:port  -> 192.168.x.x:2181 디폴트 포트
    
   #### kafka-manager 실행
     ./bin/kafka-manager
     
     
     
   #### 확인 
     http://카프카 매니저 설치 IP:9000/

도움 주신 곳 - 정말 감사합니다. 

도커로 설치 
https://m.blog.naver.com/PostView.nhn?blogId=occidere&logNo=221390946271&proxyReferer=https%3A%2F%2Fwww.google.com%2F
카프카 매니저 설치 
https://m.blog.naver.com/PostView.nhn?blogId=occidere&logNo=221395731049&proxyReferer=https%3A%2F%2Fwww.google.com%2F
카프카 전반적인 설치 내용 
https://github.com/itmare/kafka/tree/master/practice

