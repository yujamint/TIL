## Git

VCS (Version Control System) == SCM (Source Code Management)

### **git objects type**

- Blob : 파일 하나의 내용에 대한 정보
== 찍은 사진에 대한 피사체
- Tree : Blob이나 Subtree의 메타데이터(디렉토리 위치, 속성, 이름 등)
== 사진을 찍었을 때의 설정값(조리개 값 등)
- Commit : 커밋 순간의 스냅샷
== 피사체와 메타데이터가 합쳐진 jpg 파일

### **git Process Flow and Command**

Local(작업 중인 컴퓨터)과 Remote(Github)으로 나뉜다.

1. working directory에서의 변경사항을 stage에 올린다. **git add**
== 이삿짐을 용도별로 박스에 보관한다. ex) 주방용품, 욕실용품
2. stage에 올려놓은 blob과 metadata를 합쳐 commit을 만들고, 이를 local repository에 저장한다. **git commit**
== 이삿짐을 트럭에 싣는다.
3. local repository에 쌓아놓은 commit을 remote에 넘긴다. **git push**
== 트럭이 목적지로 이동

### **Cloud Remote Repository Services**

- Github : Microsoft에 인수된 가장 유명한 서비스
- Bitbucket : Atlassian이 서비스, jira, trello 등의 부가도구와 유기적
- Gitlab : 사설 서버 구성 가능

Git과 Github은 엄연히 다르다!!

### **Start project with clone**

git clone “원격 저장소(github repository) 주소” → 만들어진 원격 저장소를 로컬로 가져온다.
git clone을 실행하여 저장소가 됐다면, 다음과 같이 실행된다.

1. ls -a를 했을 때, **.git** 파일이 있다
- 숨겨져 있는 .git 파일을 찾기 위해 -a 옵션과 함께 ls 명령어를 실행한다.
2. git status 명령어를 입력했을 때, On branch main~ 등의 메시지가 출력된다.
- 저장소가 아니라면, fata: not a git ~ 오류메시지가 출력된다.

README.md : 프로젝트를 전반적으로 설명하는 대문 역할.

### **Practice**

1. 새 파일 생성 : menus.md
2. 오늘 저녁메뉴로 먹고 싶은 음식 markdown format에 맞춰 작성
3. git add, commit, push

### Commit 할 때의 주의사항

git add를 통해 작업 단위 구분을 잘해줘야 한다. → A 파일 수정 내용과, B 파일 수정 내용을 각각 다른 commit으로 만든다.

### **Conventional Commits**

1. commit의 제목은 commit을 설명하는 40자 내외의 구나 절로 완성
2. importanceofcapitalize → Importance of Capitalize
3. prefix 꼭 달기

어떤 내용의 작업을 했는지 알아보기 쉽도록 commit 메시지를 작성한다.

- prefix
    - feat : 기능 개발 관련
    - fix : 오류 개선 혹은 버그 패치
    - docs : 문서화 작업
    - test : test 관련
    - conf : 환경설정 관련
    - refactor : 리팩토링 관련
    - build : 빌드 관련
    - ci : Continuous Integration(지속적 통합) 관련

### .gitignore

git이 특정 파일/폴더를 추적하지 않도록 명시하기 위해 작성한다.

- hidden 폴더 내의 모든 파일을 추적하지 않도록 하고 싶을 때
→  .gitignore 파일에 “hidden/**” 작성 : 애스터리스크 하나만 사용해도 가능하지만, 레퍼런스 문서에서는 두 개를 사용하도록 권장한다.

[gitignore.io](http://gitignore.io) 에서 본인이 사용하는 개발 환경, 프레임워크 등을 추가한 뒤에 파일을 생성하면 본인에게 맞는 gitignore 파일을 만들어준다.

→ 각 OS(Windows or Mac)의 썸네일 파일이 레포지터리에 올라가는 것을 방지한다.

github에서 repository를 생성할 때 template 추가를 통해 gitignore파일을 생성할 수도 있지만, gitignore.io에서 만드는 것을 추천

### **LICENSE**

- MIT License : MIT에서 만든 라이센스로, 모든 행동에 제약이 없으며, 저작권자는 소프트웨어와 관련한 책임에서 자유롭다.
- Apache License 2.0 : Apache 재단이 만든 라이센스로, 특허권 관련 내용이 포함되어 있다.
- **GNU General Public License v3.0** : 가장 많이 알려져있으며, 의무사항이 존재한다.
    - 의무사항 : 해당 라이센스가 적용된 소스코드 사용시 GPL을 따라야 함
    - 주의해야한다!

라이센스는 리포지터리를 생성할 때 추가할 수 있다.
이미 생성한 리포지터리에 대한 라이센스는 리포지터리 세팅에 들어가서 추가 가능

### git 파일 추적

파일의 내용을 변경하게 되면 git이 이를 탐지하지만, 디렉토리는 객체가 아니라 개념, path로서만 존재하기 때문에 디렉토리를 생성하고 git status 명령어를 사용해봐도 변경 내용이 탐지되지 않는다.

git status -uall : Untracked files에 폴더명까지만 출력하지 않고, 폴더 내부의 어떤 파일이 변경되었는지 출력한다.
