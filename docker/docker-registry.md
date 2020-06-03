# Docker registry

Docker build 를 통해서 생성한 image를 공유하기 위한 저장소이다.

Docker hub등과 같은 public registry에서는 공개적으로 image를 공유할 수 있고, 

사내에서만 공유하고 싶은 경우 등에는 private registry를 생성해 image를 공유할 수 있다.

아래에서는 private registry를 생성하는 방법에 대해 다루려고 한다.

## Docker registry installation 

도커가 설치되었다고 가정하면, docker pull 명령어로 docker registry image를 받는다.

''' 
$ docker pull registry:latest
'''
