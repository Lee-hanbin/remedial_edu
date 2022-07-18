##프로젝트에 대한 설명문서
- github프로젝트에서 가장 먼저 보이는문서
- 일반적으로 소프트웨어와 같이 배보되는 파일
- 파일의 확장자 이름 : .md ===> 마크다운형식을 사용한다.

현재 README.md 파일이 있는 윈도우 탐색기의 경로(디렉토리)
이 경로를(현재 이 폴더가 있는 공간)을 버전 관리 하겠다.
git init
현재 이 위치를 로컬 저장소 (내 컴퓨터의 저장소 역할을 하도록 한다.)

현재 위치에 있는 파일들의 목록을 출력해주는 명령어
ls
이 명령어를 통해 확인한 파일들을 버전관리 하겠다.
==> git을 사용해서 버전관리를 하겠다.

이 파일의 역사(히스토리)
수정내역, 수정한 날짜, 누가 수정했는지 등등 ...
이런것들을 저장하는 일 ==> 버전관리를 한다.
특정 버전으로 남기면 위에 있는 내용들을 기록으로 남긴다
기록을 남긴다 ==> commit(커밋)한다.

커밋이라는 작업은 3가지 영역을 통해서 동작하게 한다.
3가지 영역
-working directory
내가 작업하고 있는 실제 디렉토리
(버전관리할 파일들이 모여있는 폴더의 위치)
=> untracked 파일 => 버전관리되고 있는 파일은 아님
-staging area
커밋으로 남기고 싶은, 특정 버전으로 관리하고 싶은 파일이 있는 곳이다.
==> 커밋할 준비가 되어있는 파일들이 커밋 되기전에 존재하는 영역
커밋할 준비가 되어있다 ==> 버전관리할 파일이다.
=>git add를 통해 파일을 staging Area로 넘기고 이때, 파일은 staged 파일
-repository
어떤 파일을 커밋을 하게되면 이 레파지토리 영역에 올라오게 된다.
여기는 커밋들이 저장되는 곳, 버전관리되는 파일들이 실제로 저장된 곳
=> git commit을 통해 repository로 옮겨주고 => tracked 파일로 분산관리되고 있는 파일

처음 된 commit하면 commit_01 파일이 남고
파일을 수정해서 다시 commit하면 commit_02로 남는다.


git add 파일이름 
=> 해당 파일을 staging area로 이동 시켜서 커밋준비를 한다.
git add .
=> 현재 작업 영역 (working directory)에서 버전 관리 되고 있지 않은 모든 파일들을  staging area로 이동시킨다.

브랜치 master
master : 우리가 커밋을 제일 처음 했을 때 원본이 있는 공간

브랜치 추가
브랜치 new1
new1 : master 브랜치에서 원본 파일들을 그대로 복사해온다
그 변경사항은 new1이라는 브랜치에만 존재
master 브랜치에 있는 원본 파일은 변경내역이 기록되지 않는다.
(똑같은 작업 영역에 대해서 레포지토리를 두 개 가지고 있는 효과)
나중에 merge 브랜치 두 개를 합쳐서 통합시킨다.
== new1에 있는 변경사항이 master에 기록이 된다.

*** plese tell me who you are ***
=> 처음 커밋을 진행하게 되면 나오는 메세지
=> 누구인지 알아야 누가 해당 파일을 커밋했고, 변경사항을 기록했는지를 알 수 있음.

git config --global user.name "너 이름"
git config --global user.email "너 이메일"

--global
=> 전역적으로 설정한다.
(다른 디렉토리, 작업영역에서도 지금 내가 설정한 user.name과 user.email을 동일하게 사용할게)

-git branch new_저장소 ==> 새로운 branch 만듦
-git branch -D new_저장소 ==> brnach 삭제
-git checkout new_저장소 ==> new_저장소로 버전을 옮김
-git checkout master ==> master로 다시 옮김

git remote add origin "URL"
=> 인터넷을 연동해서 원격 저장소에다가 로컬에 있는 파일들(커밋내역들을 저장)
=> url로 원격 저장소를 식별
remote : 원격 저장소에 어떤 설정을 할 것이다.
add : 원격 저장소 추가
origin : 추가할 원격저장소의 이름
url : 원격 저장소가 위치한 주소(url) <-- 여기에 파일을 저장



git push origin master
=> 내가 push를 해서 원격 저장소에 변경내역을 저장했다.
push : 원격 저장소에 커밋 내용을 동기화시킨다.(저장한다.)
origin : push할 원격 저장소의 이름
master : 그 저장소의 어떤 브랜치에 변경내역을 저장할건지 (기본은 master)

다른 컴퓨터의 사용자는 해당 변경내역을 어떻게 최신화 할까?


git clone : 최초 1번만 실행하는 명령어
이미 init 되어있는 다른 repository를 복사해서 가져오겟다

git pull : 지금 이 경로에 이미 repository가 init 되어 있거나 clone되어 있는 상태에서 현재 내 파일이 오래되었을 수도 있으니, 다른 사람들이 원격저장소에 저장한 변경내역들을 가져와서 내 파일들을 최신화 시키겠다.
변경한 적이 있을 때마다 실행되어지는 명령어가 된다.
다른 사람들이 push를 통해 원격저장소에 변경내역을 저장했다.
==> 나는 pull을 통해 다른 사람들이 저장한 변경내역을 내 로컬 레포지토리로 가져와서 최신화 하겠다.
git pull origin master
origin : 변경내역을 최신화할 원격 저장소의 이름
master : 해당 원격 저장소의 어떤 브랜치를 최신화 할건지

***정리 ***

1. git init => 현재 내가 작업하고 있는 영역을 repository로 사용한다.
2. git add  => 현재 내가 작업하고 있는 영역의 모든 파일을 버전관리하겠다.
3. git commit -m 'commit message' => 메세지를 남겨서 변경내역을 저장
4. git remote add origin "url" => 원격저장소의 url을 이용해서 해당 원격 저장소에 현재 작업하고 있는 로컬 저장소(init 명령어를 실행한 곳)을 연동하는 명령어
5. git push origin master => 원격 저장소에 현재 커밋한 내역(변경사항) 최신화

다른 곳으로 레포지토리 복사
git clone "url" : 해당 url을 가진 원격 저장소 내의 파일들을 복사해온다.
git pull origin master : origin 이라는 이름을 가진 원격 저장소에서 master 브랜치에 있는 파일들을 최신화 하겠다.

수고하셨습니다.
