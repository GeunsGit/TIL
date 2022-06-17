# TIL

## Jenkins + docker를 활용한 CI/CD 구축

1. Docker로 Jenkins를 설치하고 설정하기
2. Gitlab과 Jenkins 연동하기
3. 웹서버(Nginx) 설치 후 어플리케이션 배포하기

### CI / CD

- Continuous Integration(지속적인 통합), Continious Delivery(지속적인 서비스 제공), 또는 Continuous Deployment(지속적인 배포)의 약자
- 애플리케이션 개발 단계를 자동화하여 애플리케이션 개발을 보다 짧은 주기로 고객에게 제공하는 방법이다.
- CI/CD는 애플리케이션 통합, 테스트, 제공, 배포에 이르는 라이프사이클 전체에 걸친 지속적인 자동화와 모니터링을 제공한다.

## Docker
**Docker**는 컨테이너 기반의 오픈소스 가상화 플랫폼이다.
기존의 온프레미스 환경에서 서버 구축의 어려움을 Docker-Engine 위에서 Docker-Registry를 통해 Docker-Images를 Docker-Compose로 쉽게 구성 및 관리할 수 있게 구축해주는 기술이다.


- Docker 설치(https://docs.docker.com/get-docker/)

![image](/uploads/af505eb7c2015cae1391f8385bfa05aa/image.png)

- Docker를 이용해 Jenkins를 설치한다.

![image](/uploads/c109907f57ac8c10811926f5f2b1c117/image.png)

- admin 비밀번호를 입력한다.
- admin 비밀번호는 Jenkins를 설치할 때 생기는 로그에 있다.
- Docker의 로그 확인
```
docker logs jenkins
```

![image](/uploads/de338ff8506cbefd018e973220bbfd20/image.png)

- 위 과정을 마치면 Docker로 Jenkins 설치가 완료된 것이다.

## Jenkins 플러그인 설치

- 지속적인 통합, 지속적인 배포를 도와주는 대표적인 툴이다.
- https://www.jenkins.io/

![image](/uploads/12b6a5e2c7dd957b0f541d5654a471e1/image.png)
![image](/uploads/428826af7455b72ea47d05c8343864af/image.png)

- Plugin Manager로 이동해 gitlab플러그인과 docker플러그인을 설치한다.

## Jenkins 컨테이너안 도커 설치

- 컨테이너 형태로 설치된 Jenkins 안에서 docker 명령어 실행을 위해 docker를 설치한다.
- 쉘을 통해 컨테이너로 접근해 설치한다. 다음 명령어로 접근할 수 있다.
```
docker exec -it jenkins bash
```
- docker 설치 확인
```
docker --version
```

## 도커라이징 및 배포 설정

- 이전에 만들었던 vue-cli 프로젝트를 도커라이징하여 배포한다.

![image](/uploads/745a078845c110523d78ce23faf3006c/image.png)
- Dockerfile 생성
- 그 다음 Jenkins에서 새로운 프로젝트를 프리스타일 타입으로 생성한다.

![image](/uploads/9eb1b6e26cc3225a2565d4b84c930af3/image.png)
- 배포될 Repository URL 주소를 입력하고, Credentials에 계정 정보를 입력해준다.

![image](/uploads/ddb1a87a39cd12c499fed2cc3dfe7307/image.png)
- repository에 새로운 push가 들어오면 자동으로 빌드가 되도록 설정한다.

![image](/uploads/97d9f3270f8230d016a5836b161b10e6/image.png)
- 빌드 섹션에서 쉘 스크립트 실행을 선택 후 다음과 같이 스크립트를 넣어주었다.(예시사진)

![image](/uploads/224dea24a47bd361e12556b6667d67d4/image.png)
- Build Now를 누른다.

![image](/uploads/6263000458c4b74c401b542892b02c04/image.png)
- 다음과 같이 뜨면 정상적으로 빌드에 성공한 것이다.

![image](/uploads/66c609d83148c01f20dba5559a8faf86/image.png)
- 이전에 만들었던 vue-cli 프로젝트를 성공적으로 빌드 완료했다.

## 배운점 / 느낀점
Docker로 Jenkins 설치 및 설정, 그리고 내 Gitlab과의 연동 후 배포까지 일련의 과정을 모두 경험해 보았다.
완성된 서비스를 배포하는데는 여러가지 전략과 방식이 있는데, 오늘 실습해본 Docker로 Nginx를 이용한 배포도 그 중 하나였다.