# 2023-OSS-TEST

# 6-1 원격 저장소 복제 clone
## 01 지역에서 깃허브 원격 저장소 복제 clone

원격 저장소를 지역 저장소에 복제(clone)
- 공개된 저장소는 소유와 관계 없이 누구나 가능

깃허브 원격 저장소 생성
- 저장소이름 git-clone
- https 주소 복사

PC 깃에서 원격저장소 복제(git clone)
- $ git clone [복사된-주소] : 원격저장소와 동일한 이름으로 복제
- $ git clone [복사된-주소][새로운-폴더명] : 하부 폴더 새로운 폴더명으로 복제
- $ git clone [복사된-주소] : 현재 폴더에 바로 복제

원격 저장소 별칭 이름 점검
- $ git remote : 원격 저장소 목록 -> 기본 이름 origin 점검 -> 위에어 clone을 했기 때문에 origin이 위의 주소가 설정
$ git remote -v
- 저장소 주소 등 원격 저장소 정보 목록 표시

깃에서 복사 실행
- $ git clone 저장소주소 [저장소폴더명]
자신의 지역 저장소에 복사 명령
- $ git clone http://github.com/username/git-clone.git

원격 저장소 이름과 복제되는 지역 저장소 이름 다르게
- $ git clone https://github.com/ai7dnn/git-clone.git 하부폴더명_다른저장소이름 : 하부 폴더 지정해서 복사
- $ git clone https://github.com/ai7dnn/git-clone.git . : 현재 폴더에 복사

 원격 저장소 별칭 관리
 - $ git remote add origin URL : 원격 저장소 별칭 저장
 - $ git remote show origin : 자세한 정보
 - $ git remote rename origin org : 이름 수정
 - $ git remote rm org : 삭제

원격 저장소 복제
- $ git clone https://github.com/atom/atom.git
- $ git clone https://github.com/atom/atom.git .
- $ git clone https://github.com/atom/atom.git mytest

원격 저장소의 모든 브랜치 보기 가능
- $ git remote show origin(atom)

## 02 유명 오픈소스 소프트웨어 복제

유명 OSS
- 네트웍이 느리면 복제가 어려울 수도
- 편집기 vscode
- 편집기 atom
- VCS 깃
- 구글 인공지능라이브러리

Vscode 배시 열어 명령어로 실행
- $ git clone https://github.com/microsoft/vscode.git

# 6-2 지역과 원격 저장소 연동 push pull
## 01 개인 접근 토큰(Personal Access Token) 생성

개인 접근 토큰 인증 개요
- 개인 프로젝트를 진행하던 중 아래와 같은 에러 메시지가 발생
- 비밀번호 인증 대신 사용하는 강화된 인증 방법
- 깃허브 계정마다 토큰 생성 필요

## 02 깃허브 원격 저장소 수정 후 pull

깃 깃허브 push pull
- 올리기 내리기

원격 저장소 수정 후 지역 저장소에서 pull
- 깃허브 원격 저장소에서 수정 후 커밋

윈도 push 중 오류
- 참조 오류 발생 가능
- 인증 오류 발생 가능
- Windows 환경에서 깃 사용자 계정과 암호 설정 및 변경
-- 1. 제어판 - 사용자 계정 - 자격 증명 관리자
-- 2. Windows 자격 증명
-- 3. 일반 자격 증명
-- 4. git 관련 자격 증명 편집

인증 오류 해결 방법
- PAT(Personal Access Token)로 연결
-- $ git push -u https://{token}@github.com/{username}/{repo_name}.git
-- $ git push -u https://ghp_GeU8yVKNmKdIpZ787LHDb6HARqF8h@github.com/
ai7dnn/git-clone.git

## 03 지역에서 원격 저장소로 push

지역 저장소에서 push
- 쓰기 권한이 있어야 push가 가능 : 자신의 저장소나 다른 사람의 저장소라면 협업자로 등록
- Push : 로컬 저장소에서 남겨놓은 코드 변경 이력들이 원격 저장소로 전송
- 명령 - $ git push <저장소별칭명> <브랜치명>

명령 push에서 인자 생략하기
옵셩 -u 사용
- 최초에 한 번만 저장소명과 브랜치명을 입력하고 그 이후에는 모든 인자를 생략 가능 : $ git push origin topic
- 성공 이후 간단히 다음으로 가능 : $ git push
대부분의 경우에는 로컬 저장소와 원격 저장소에서 동일한 브랜치 이름을 사용하기 때문에 항상 현재 브랜치를 기준으로 git push 명령어가 작동한다면 매우 편리
- 설정 변수 push.default 를 current로 설정 : $ git config --global push.default current
- 어느 브랜치에서 작업을 하든 git push만 날리면 원격 저장소에 동일한 브랜치로 코드 변경이 업로드 : $ git push

git pull = git fetch + git merge
git pull 명령
- fetch 명령과 병합하는 merge 명령이 순차적으로 진행
- fetch 명령 : 원격 저장소의 정보를 로컬(remote/origin) 저장소로 가져오는 명령
- merge 명령 : 변경된 정보를 로컬 저장소의 내용과 병합
fetch 명령으로 작업한 내용을 확인한 후
- merge 여부를 결정하는 과정 : 병합(merge) -> 다른 브랜치의 내용을 합침

fetch
- 원격 저장소에서 로컬 저장소로 소스를 가져와 병합을 미수행하는 명령
-- 단지 소스를 가져올 뿐 병합을 하지 않음
- 명령어
-- $ git fetch <remote>
--- $ git fetch origin
- fetch후 이후 origin/main, origin/HEAD가 더 최신의 위치에 있음
-- 지역인 HEAD의 main이 이후에 있음 : $ git log --all --oneline --graph

fetch 후 병합
- 깃허브의 내용을 반영하려면 fetch 후 merge 해야함 : $ git merge origin/main

원격 브랜치
원격을 포함한 모든 브랜치 파악
- 지역의 브랜치와 HEAD : main HEAD
- 원격의 브랜치와 HEAD : origin/main origin/HEAD

# 7-1 오픈소스 소프트웨어 개요
## 01 오픈소스 소프트웨어 개요

$ 오픈소스 소프트웨어의 의미
- 소프트웨어의 소스코드를 자유롭게 읽고, 수정 및 재배포가 가능

오픈소스 소프트웨어 개발을 지원하는 서버인 깃허브에서의 협업 방식
- github, gitlab, bitbucket

대표적인 오픈소스 소프트웨어
- 파이썬, 사이킷런, 파이토치, 텐서플로, MySql, 몽고DB 등

## 02 오픈소스 소프트웨어 저작권

오픈소스 소프트웨어의 저작권을 이해할 수 있다.
- 의무 강도에 따른 분류
- GPL, LGPL, Apache, BSD, MIT 순으로 의무 강도가 낮아짐

# 7-2 임시저장 stash
## 01 깃 4영역과 임시 저장 개요

깃 4영역
- 깃 3영역 + stash 영역
 
깃 영역의 가장 단순한 상태
- Nothing to commit, working tree is clean
 
Git Stash
사전적 의미 stash
- 놓다, 남겨두다, 감추다, 안전한 곳에 숨겨두다
- 커밋할 필요 없이 파일의 변경 사항을 숨기거나 비밀리에 저장할 수 있는 강력한 도구
-- 작업 디렉토리와 스테이징 영역의 원래의 내용을 stash 스택에 저장
-- 작업 디렉토리와 스테이징 영역의 값을 깃 저장소의 마지막 커밋 내용으로 복사
- 따로 안전한 곳에 저장했다가 다시 가져올 수 있는 기능
-- 저장 내용 -> 작업 디렉토리 내용과 스테이지 내용

Stash 저장 구조
깃에서 임시 저장소(스택 구조)에 저장
- Stack of git stashes : 가장 최근의 내용이 가장 위에 저장되는 구조

Git stash 필요성
브랜치 이동 또는 이전 커밋으로 이동하려면 커밋할 게 없고, 작업 트리가 깨끗해야 함
- $ git switch bname
- $ git checkout HEAD~
수정한 내용이 있거나 커밋할 게 있는 상황에서 다른 브랜치 이동 또는 이전 커밋으로 이동하려면 현재 작업 공간의 수정 내용과 인덱스의 내용을 보관할 필요가 있음
- 나중에 다시 사용하기 위해

임시저장 영역에 저장되는 내용
 stash로 저장되는 내용
 - 작업 디렉토리 내용과 스테이징 영역 내용이 stash에 저장되고 작업 디렐토리 내용과 스테이징 영영 내용이 최신 커밋 자료로 남음

## 02 임시 저장 명령 stash

작업 폴더와 스테이징 영역을 숨김(stash)에 저장하고 작업 폴더를 정리
- $ git stash
- $ git stash –m ‘메시지’
- $ git stash save
- $ git stash save ‘메시지’

옵션
- --keep-index, -k : 스테이징 영역은 제외하고 작업 폴더만 저장
- --include-untracked, -u :Untracked 파일도 포함해 저장

최근 또는 지정된 임시저장소 내용을 가져와 반영하고 삭제
- $ git stash pop
- $ git stash pop stash@{n}

최근 또는 지정된 임시저장소 내용을 가져와 반영, 작업 디렉토리만 반영, stash 목록은 그대로
- $ git stash apply
- $ git stash apply stash@{n}

최근 또는 지정된 임시저장소 내용을 가져와 반영, 작업 디렉토리와 스테이징 영역도 반영, stash 목록은 그대로
- $ git stash apply --index 
- $ git stash apply --index stash@{n}

임시저장 목록 보기
- $ git stash list

커밋 자료와 최신 stash 항목 간의 차이로 표시
- $ git stash show
- $ git stash show –p

커밋 자료와 해당 stash 항목 간의 차이로 표시
- $ git stash show stash@{n}
- $ git stash show stash@{n} -p

최근 임시저장 내용을 삭제
- $ git stash drop

지정된 임시저장 내용을 삭제
- $ git stash drop stash@{n}

모든 stash 목록을 모두 제거
- $ git stash clear

# 8-1 다양한 브랜치 병합
## 01 브랜치 병합 개요

기준 브랜치에서 hotfix 브랜치 병합
- $ git merge hotfix
-- fast-forward, 3-way merge

무조건 3-way 병합 수행
- $ git merge --no-ff hotfix

fast-forward인 경우에만 병합 진행
- $ git merge --ff-only hotfix

## 02 병합의 다양한 옵션

현재 브랜치에서 커밋 하나만 생성해서 병합
- $ git merge --squash hotfix

# 8-3 병합 충돌과 해결
## 01 병합 충돌

3-way 충돌 발생
- $ git merge hotfix
  
## 02 충돌 해결

충돌한 파일을 인지하고 파일 수정
- $ code file

수정 후 다시 add, commit
- $ git commit –am ‘msg’

충돌 이후 병합 취소
- $ git merge --abort

# 9-1 브랜치 리베이스 rebase
## 01 병합 rebase

기준 브랜치에서 main 브랜치 rebase 병합
- $ git checkout topic
- $ git merge main

## 02 3-way, fast-forward와 rebase 비교

다시 main을 돌아와 fast-forward 병합 진행
- $ git checkout main
- $ git merge topic

git rebase <newparent> <branch>
일반적 rebase 방법
topic에서 main을 rebase 한 이후, 다시 main으로 이동 fast-forward 병합 수행
- $ git checkout topic
- $ git rebase main
- $ git checkout main
- $ git merge topic 

다른 rebase 방법: 어느 브랜치든 main topic 순서로 재배치 방법
- $ git rebase main topic
- $ git checkout main
- $ git merge topic

# 9-2 커밋 이력 수정
## 01 최신 커밋 수정

최근 커밋 메시지 수정

기본 편집기 설정 방법
- $ git config --global core.editor ‘code --wait’

설정된 편집기로 최근 커밋 메시지 수정
- $ git commit --amend : 새로운 커밋 ID로 수정됨

최근 커밋 메시지를 직접 입력해 수정
- $ git commit --amend -m "an updated commit message“ : 새로운 커밋 ID로 수정됨

커밋 옵션 --amend 사용

기본 편집기로 메시지 편집
- $ git commit --amend

명령어 상에 직접 메시지 입력
- $ git commit --amend –m 'new message‘

메시지 수정 없이 다시 커밋 수정
- $ git commit --amend --no-edit

## 02 rebase -i로 여러 커밋 수정

이전 커밋 HEAD~2..HEAD까지 각각의 커밋을 수정
-  $ git rebase --interactive HEAD~3

주요 rebase –i 대화형 명령어
- p(ick): 해당 커밋을 수정하지 않고 그대로 사용
- r(eword): 개별 커밋 메시지를 다시 작성
- s(quash): 계속된 이후 커밋을 이전 커밋에 결합
- d(rop): 커밋 자체를 삭제

# 9-3 비주얼스튜디오 코드의 깃 활용
## 01 Vscode에서 깃 활용 기초
## 02 Vscode에서 파일 비교 git diff

수정 작업 취소
- $ git restore
- $ git restore --staged

작업 영역과 스테이지 영역 파일 수정 취소
- 명령어 git restore : 옵션 --staged : index 파일 unstage(index를 최근 커밋으로 수정[복사])

작업 영역 수정 취소
- 현재의 index 파일로 수정 : $ git restore h.txt

스테이지 영역 수정 취소
- 현재의 최근 커밋 파일로 수정, unstage : $ git restore --staged h.txt

# 10-1 버전 되돌리기 reset
## 01 버전 되돌리기 reset과 옵션

HEAD~2의 내용으로 작업 디렉토리와 스테이징 영역, 깃 저장소에 복사
- $ git reset --hard HEAD~2

HEAD~2의 내용으로 스테이징 영역과 깃 저장소에 복사
- $ git reset --mixed HEAD~2

HEAD~2의 내용으로 깃 저장소에 복사
- $ git reset --soft HEAD~2

이전에 수행한 reset을 바로 취소하는 명령
- $ git reset --hard ORIG_HEAD

## 02 reset 정리, checkout과 reset 비교

reset의 3가지 방식

git reset —옵션 commit ID
—hard
- 인자인 커밋 깃 저장소의 내용을 작업 폴더와 스테이지 영역, 그리고 깃 저장소에 모두 복사 수정 (3)
—mixed
- 기본 옵션으로 스테이지 영역과 깃 저장소 두 곳에 복사 수정 (2)
—soft
- 깃 저장소에만 복사 , 수정 하므로 **작업 폴더와 스테이지 영역은 이전 내용이 그대로 남음** (1)

커밋 되돌리기

git reset <옵션> <돌아가고 싶은 커밋>

hard , mixed , soft 세가지
—soft
- 바로 다시 커밋할 수 있는 상태로 남아있음
- **다시 마지막 이전 head로 돌아가려면 commit 만 필요**

—mixed
- 이력은 되돌려지고 , 인덱스도 되돌가는 커밋의 내용으로 초기화
- 다시 마지막 이전 head로 돌아가려면 add ,commit이 필요

—hard
- 돌아가려는 이력 이후의 모둔 내용을 삭제
- 다시 마지막 이전 head로 돌아가려면 파일수정,add,commit 필요

reset 후 다시 바로 이전 상태로 되돌아가기
‘ORIG_HEAD’ 이용하면 매우 간단
- 바로 이전 커밋 참조
- git reset —hard ORIG_HEAD

reset과 checkout 비교
git reset 9033
- 브랜치의 마지막 커밋을 수정하는 명령
git checkout 9903
- HEAD 포인터를 브랜치 마지막 커밋 이전으로 이동하는 명령
summary

HEAD~2 작업 디렉토리 | 스테이지 영역 | 깃 저장소 에 복사
- 작업 디렉토리,스테이지 영역, 깃 저장소 : git reset —hard HEAD~2
-스테이지영역, 깃 저장소 : git reset —mixed HEAD~1
- 깃 저장소 : git reset —soft HEAD~2

이전에 수정한 reset을 바로 취소하는 명령

git reset —hard ORIG_HEAD
