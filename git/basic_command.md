# git command

> git 기초 정리



## 설정

### init

- `git init` 
- 폴더를 git으로 관기하기 위해 `.git` 폴더를 생성하는 명령어
- 최초에 한번만 실행하면 된다.



### status

- `git status`
- 현재 git의 상태를 출력



### log

- `git log`
- 현재 쌓여있는 commit history를 출력
- `git log --oneline`: 한 줄로 log를 보여줌(commit_id  commit_메세지)



### diff

- `git diff`
- 마지막 commit과 지금 working directory의 상태를 비교



### remote add

- `git remote add <별명> <주소>`
  - `git remote add origin URL`
- 원격저장소 주소를 등록



## 조작

### add

- `git add <파일이름>`
  - `<파일이름>`에 `.`을 입력하면 전체파일이 추가된다.
- working directory에 있는 파일을 staging area(INDEX)에 올림



### rm

- `git rm <파일이름>`
  - 로컬 디렉토리와 git 저장소에서 모두 삭제
- `git rm --cached <파일이름>` 
  - git 저장소(staging area, repository)에서만 삭제
  - 처음으로 add한 파일을 취소할 때 주로 사용



### restore

- staging area에 있는 파일을 제거

- 처음이 아닌 파일을 add한 것을 취소할 때



### reset

- `git reset --hard <커밋 id>`
  - 커밋 id는 `git log --oneline`에서 확인
  - 커밋과 파일 모두 커밋id상태로 돌아간다.
- `git reset --soft <커밋 id>`
  - 커밋을 커밋id상태로 돌아간다.
  - 하지만 staging area에는 그대로 남아있다.(add는 한 상태임)

- `git reset <커밋 id>`
  - 커밋을 커밋id상태로 돌아간다.
  - soft와는 다르게 working directory에만 남아 있다.(add부터 해야함)



### commit

- `git commit -m "커밋메세지"`
- staging area에 올라간 파일들을 스냅샷으로 저장
  - `git commit --amend`
  - 최근 commit을 취소하여 staging area로 다시 보내기 때문에 수정 후에는 원래 staging area에 있던 파일과 함께 repository로 보내게 된다.
  - `vim` 텍스트 에디터로 들어가게 되어 커밋메세지를 수정할 수 있다.
  - `i`: 입력모드로 변환
  - `Esc`: 입력모드 종료
  - `:wq`: write quit, 수정 종료



### push

- `git push <원격저장소 이름> <올릴 브랜치 이름>`
  - `git push origin master`
- commit history를 원격 저장소에 업로드



### clone

- `git clone URL 폴더이름(생략 가능) `
- git을 통해 다른 사람의 프로젝트 폴더를 복제



### pull

- `git pull origin master`
- 다른 사람이 push한 코드를 다운로드



## 필수 파일

### README.md

- 프로젝트 설명



### .gitignore

- 자동 생성되는 찌꺼기 파일들이 git에 업로드되는 것을 막아줌.
- [gitignore.io](https://www.toptal.com/developers/gitignore)
  - 생성 후 나온 페이지의 글자를 복사하여 .gitignore에 붙여넣기