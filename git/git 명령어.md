# git 명령어



### git checkout

```
$ git checkout <ref>
```

- `HEAD`의 위치를 `ref`로 바꿔준다.

- ```
  $ git checkout -b <branch> <ref>
  ```

  - 브랜치를 생성한 후 `HEAD`위치를 `branch`로 바꿔준다.
  - `ref`가 원격 브랜치인 경우, `branch`가 `ref`를 추적한다.



### git rebase

```
$ git rebase <ref1> <ref2(HEAD)>
```

- `ref2`가 있는 커밋부터 `ref1`와의 공통 부모 커밋 전까지의 모든 커밋들을 `ref1`아래로 복사해서 떨궈놓는다.

- `merge`와의 차이점은 rebase을 사용하면 커밋트리가 한줄로 되기 때문에 깔끔해지지만 커밋의 순서가 바뀔 수 있다.

- ```
  $ git rebase -i <ref1> <ref2(HEAD)>
  ```

  - `vim`과 같은 텍스트 편집기를 통해서 rebase할 커밋들을 정하고 순서를 바꿀 수도 있다



### git reset

```
$ git reset --hard <ref>
```

- 브랜치가 커밋을 하지 않은 것 처럼 예전 커밋을 가리키도록 이동시킨다.



### git revert

```
$ git revert <ref>
```

- `ref` 커밋의 반대 내용을 가진 새로운 커밋을 추가한다.



### git cherry-pick

```
$ git cherry-pick <ref> <ref> ...
```

- 복사하고 싶은 커밋을 `HEAD`아래에 추가할 수 있다.



### git commit

```
$ git commit --amend
```

- 커밋을 수정한다.



### git branch

```
$ git branch -f <branch_name> <ref>
```

- 브랜치를 `ref`로 이동시킨다.
- 브랜치가 없으면 새로운 브랜치를 `ref`에 생성한다.

```
$ git branch -u origin/main foo
```

- `foo`브랜치가 `origin/main`을 추적하도록 설정
- `foo`브랜치가 현재 작업중인 브랜치이면 생략 가능하다.



### git remote

```
$ git remote prune origin
```

- 로컬저장소에서 필요없는 origin/branch들을 제거해준다.
- `git remote prune origin --dry-run` 옵션을 주면 제거할 origin/branch의 목록을 보여준다.



### git tag

```
$ git tag <tag_name> <ref(HEAD)>
```

- `ref`에 태그를 지정한다.
- 태그는 커밋 트리에서 특정 지점을 표시하기 위한 역할을 한다.



### git describe

```
$ git describe <ref(HEAD)>
```

- `ref`와 가장 가까운 부모 태그와의 거리를 알려준다.
- `<tag>_<num>_g<hash>`



### git fetch

```
$ git fetch 
```

- 원격 저장소에는 있지만 로컬에는 없는 커밋들을 다운로드 받는다.

- 모든 원격 브랜치가 가리키는 곳을 업데이트한다.

- 로컬 브랜치는 업데이트하지 않는다.

- ```
  $ git fetch <remote> <branch>
  ```

  - 지정한 원격 브랜치만 업데이트

- ```
  $ git fetch <remote> <source>:<destination>
  ```

  - 원격 저장소의 `source`를 로컬저장소의 `destination`으로 다운로드한다.
  - `source`를 비우면 새로운 브랜치가 생성된다.



### git pull

```
$ git pull 
```

- `git fetch` 후 `git merge`를 한 것과 같은 결과가 나온다.

- 원격 저장소에서 로컬에 없는 커밋들을 다운로드 하고 원격 브랜치를 업데이트하고 로컬 브랜치와 병합한다.

- ```
  $ git pull --rebase
  ```

  - `git fetch` 후 `git rebase`를 한 것과 같은 결과가 나온다.
  - 로컬 저장소의 원격 브랜치가 최신화 되어있지 않아서 충돌이 발생하는 경우에 사용



### git push

```
$ git push
```

- 작업한 커밋들을 원격저장소로 보냄

- ```
  $ git push <remote> <branch>
  ```

  - 지정한 원격 저장소의 브랜치를 업데이트

- ```
  $ git push <remote> <source>:<destination>
  ```

  - `source`를 원격 저장소의 `destination` 브랜치로 푸쉬한다.
  - `source`를 비우면 원격 저장소의 `destination` 브랜치가 삭제된다.(`null`을 `destination`으로 푸쉬했으므로...)



### git fakeTeamwork

```
$ git fakeTeamwork
```

- 원격 저장소에 가장의 커밋을 생성한다.







### 상대참조

`^`: 참조의 부모 커밋을 가리킨다.

`~<num>`: num만큼의 상위 커밋을 가리킨다.

`^<num>`: num번째 부모 커밋을 가리킨다.

