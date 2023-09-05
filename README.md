# 깃 만든 사람이 먼저 할 일
### main 브런치에 최초 커밋
1. git init
2. git add .
3. git commit -m "first commit"
4. git remote add origin <URL>
5. git push origin main
### develop 브런치 생성
1. git checkout -b develop
2. git push --set-upstream origin develop
    - GitHub의 Repo 화면에 가면 Your main branch isn't protected 떠 있음 : main 브렌치의 보호가 되어있지 않기 때문에 설정해줘야 한다고 함
    - Protect this branch 클릭
    - Require a pull request before merging, Lock branch 선택
    - 이제 더이상 main에 push 못함
### 협업
1. Project 탭에 보드 생성
2. Convert to issue
3. issue에서 Create a branch 선택. e.g. feature-A
    - main <- develop <- feature-A
    - 개인이 사용하는 feature-A 브랜치에서 작업이 끝나면 develop으로 넘김. develop이 괜찮으면 main으로.
    - 즉, develop에서 feature-A 브랜치를 따오면 됨. cahnge branch source 클릭하고 develop으로 변경
    - git fetch origin
    - git checkout feature-A
4. 이제 프로젝트 시작하면 됨.

# 참여자가 할 일
1. git clone <url>
2. Project 탭에 해결하려고 하는 이슈 Convert to issue 선택 및 develop 브랜치를 따서 새로운 브랜치 생성.
    - git fetch origin
    - git checkout feature-B
3. 작업하고 add하고 commit하고 push
4. 기트허브에 들어가서 create pull request 생성
    - develop <- feature-B

# 만든 사람 및 참여자들이 할 일
1. pull request보고 요모조모 떠들기
2. Finish your review
    - 괜찮다 싶으면 Approve
    - 꽃됬다 싶으면 Request changes : 이거 하면 만든 사람에게 참여자가 풀어달라고 요청해야함. 안그러면 푸쉬가 안됨.
3. approved가 되면 merge pull request 선택하면 됨

# 충돌
1. push하고 pull request 생성 했는데 this branch has conflicts that must be resolved 즉 컨플릭트 발생.
    - 니가 따왔던 develop랑 지금은 버전이 다르단 말.
2. 컨플릭트 안내보면 command line 링크가 있음. 눌러서 따라 하면 됨.
    - git checkout develop
    - git pull origin develop
    - git checkout feature-A
    - git merge develop
        - 이때 충돌난 부분 보여줌. 누가 해당 코드 썼는지 확인해서 호출함. 이거 머꼬. 디지고 싶나. 바까라. 하고 내 코드로 바꾸면 됨. 즉 이런 충돌은 무조건 위협부터 가해야함.
        - 위협을 하고 나면 바꾸고 싶은 코드로 충돌난 부분을 수정하면 됨.
3. git add
4. git commit
5. git push
6. 이렇게 하면 pull request에 conflict 글자 사라짐. 아직 남아있으면 충돌 부분 남아있다는 말.

### 배포 (1주마다 한번 배포 담당자가 하게 됨. 즉 야근)
1. develop 브런치 new pull request 만들기.
    - master <- develop
2. 다 모이가꼬 리뷰하고 approve
3. merge
    - merging is block : 일단 무시하고 진행해도 됨. 나중에 문제가 되겠지만
    충돌 (Conflicts)
    권한 부족 (Lack of Permissions)
    보호 브랜치 (Protected Branch)
    CI/CD 실패 (CI/CD Failure)


---------------------------
main : 완벽한 코드만
develop : 개발중인 코드만