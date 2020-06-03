# Docker registry

Docker build 를 통해서 생성한 image를 공유하기 위한 저장소이다.   

Docker hub등과 같은 public registry에서는 공개적으로 image를 공유할 수 있고,     

사내에서만 공유하고 싶은 경우 등에는 private registry를 생성해 image를 공유할 수 있다.

아래에서는 private registry를 생성하는 방법에 대해 다루려고 한다.



## Docker registry 설치 

도커가 설치되었다고 가정하면, docker pull 명령어로 docker registry image를 받는다.

~~~
$ docker pull registry:latest
~~~

## Docker registry 실행

도커 레지스트리 이미지가 설치되었다면, container를 detached mode로 생성합니다.

~~~
$ docker run --name registry-private -d -p 5000:5000 registry
~~~

컨테이너가 생성되었다면, curl 명령어로 확인해볼 수 있습니다.

~~~
$ curl "http://0.0.0.0:5000"
~~~

## Docker image 생성

private registry에 저장하고자 하는 docker image를 생성해줍니다.

이미 존재하는 컨테이너를 이미지화 하려면

~~~
$ docker commit container_name image_name:image_tag
~~~

tar 형식으로 저장된 이미지를 올려주려면

~~~
$ docker load -i xxx.tar
~~~

또는

~~~
$ docker import xxx.tar image_name:image_tag
~~~

Dockerfile에서 이미지를 빌드하려면 dockerfile이 저장된 경로로 이동하여

~~~
$ docker build -t image_name:image_tag
~~~

를 입력해줍니다.

## Docker registry에 저장

이미지가 정상적으로 생성되었다면 docker registry에 push 해주어야 합니다.

이미지를 registry에 넣기 위해서는 이미지에 registry 정보에 대한 tag를 붙여주어야 합니다.

~~~
$ docker tag image_name:tag_name 0.0.0.0:5000/image_name
~~~

같은 이미지 파일이지만 새로운 이름이 부여된 것을 확인해봅니다.

~~~
$ docker image ls
~~~

이 이미지를 push해주면, tag에 지정해준 registry에 이미지가 업로드됩니다.

~~~
$ docker push 0.0.0.0:5000/image_name
~~~




