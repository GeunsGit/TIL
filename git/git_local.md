# git local 다루기

-------------
## 프로젝트 개발

* 프로젝트 개발을 위해 많은 개발자들이 협업을 하고 있다.
* 기존의 개발자들은 팀원들간에 최신버전의 관리가 힘들었고 충돌이 발생하기 일쑤였다.
* 이러한 배경에서 형상 관리 도구가 등장한다. CVS, SVN, GIT 등이 있다.
* 이러한 협업 도구를 이용해 버전관리(형상관리)를 용이하게 할 수 있다.
* 이 도구들 중 앞으로 자주 사용하게 될 git에 대해 알아보겠다.
-------------

### 특징
1. 가볍고 빠르다.
    * 코드를 공유할 때만 중앙 서비스에 접속하여 네트워크 속도와 상관 없이 빠른 작업 진행이 가능하다.
2. 각각의 개발자에게 코드가 있다.
3. Staging area 가 존재한다.

-------------
### 사용 방법
* Git Bash 실행
* Remote Repository 프로젝트 clone 가져오기
    * git clone https://github.com/~.git
* Local working directory 작업하기
* Local 파일 작업내용 staging 하기
    * git add filename
    * git status를 입력해 git의 상태를 확인하면 여전히 master(main) 브랜치에 존재한다.
    * unstaging 하려면 git restore --staged filename
* staging한 파일 커밋하기
    * git commit -m "commit message"
* staging과 commit을 동시 수행하려면 ?
    * git commit -am "commit message"
* Remote Repository 확인
    * git remote -v
* Local Working directory 작업 push
    * git push -u origin master(main)
* 만들어진 버전을 확인하려면 ?
    * git log
-------------
### 학습한 내용과 느낀 점
* git의 등장 배경과 git을 사용하며 얻는 장점을 알게 되었다.
* 원격저장소 clone 생성부터 push 까지의 과정에 대해 이해하게 됐다.
* git local 의 다양한 명령어들을 숙지하게 됐다.
* 앞으로 자주 협업하게 될 것 같아 git에 대해 충분히 숙지해야함을 느꼈다.
* 협업을 하면서 git에 대해 추가적으로 알게 된 내용을 정리해보도록 노력하겠다!