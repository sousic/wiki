#docker 기본명령어


##이미지

* docker 이미지 검색
    ```
    sudo docker search ubuntu
    ```
    
* docker 이미지 받기
    ```
    sudo docker pull ubuntu:latest
    ```
    
* docker 이미지 목록 출력
    ```
    sudo docker images
    ```
    
* docker 이미지 삭제
    ```
    sudo docker rmi ubuntu:lastest
    ```

##컨테이너
* run 명령으로 컨테이너 생성
    ```
    sudo docker run -i -t --name hello ubuntu /bin/bash
    
    ex>  docker run <옵션>      <이미지 이름> <실생할 파일>
    
    --name 으로 사용할 이름을 지정하지 않으면 docker가 임의로 이름을 지정함
    ```
    
* 컨테이너 목록 확인
    ```
    sudo docker ps -a
    
    -a 옵션을 사용하면 정지된 컨테이너까지 모두 출력하여 보여줌
    ```
    
* 컨테이너 시작
    ```
    sudo docker start hello
    
    hello는 위에서 생성한 컨테이너 이름이다. 이름대산 컨테이너ID를 사용해도 됨
    ```

* 컨테이너 재시작
    ```
    sudo docker restart hello
    ```
    
* 컨테이너 정지
    ```
    sudo docker stop hello
    ```
    
* 컨테이너 삭제
    ```
    sudo docker rm hello
    ```