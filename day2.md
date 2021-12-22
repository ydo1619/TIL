# Git 특강 2일차

#### 1. 원격 저장소 연결

```bash
$ git remote add origin https://github.com/ydo1619/TIL.git
```



#### 2. 원격 저장소 연결 여부 확인

```bash
$ git remote -v

origin  https://github.com/ydo1619/TIL.git (fetch)
origin  https://github.com/ydo1619/TIL.git (push) 
```



#### 3. Github에 파일 업로드

```bash
# 현재 상태 확인
$ git status

$ git add .

$ git commit -m "Upload day2"

# 커밋 확인
$ git log --online

$ git push origin master

$ git push -u origin master
# 이후에는 $ git push 라고만 작성해도 push 가능 / 둘 중 하나 사용가능
```



#### 4. 수정 후 업로드

```bash
$ git add .

$ git status

$ git commit -m "Update day2"   # 로컬에 저장

$ git push 						# Github에 저장
```

- 무조건 로컬에 먼저 commit하고 Gihub에 push 할 것.



#### 5. 원격 저장소 클론(clone)

```bash
# 로컬(강의실)에서

$ git clone https://github.com/ydo1619/git-remote.git
```

- 클론은 폴더 자체가 없을 때 전부 복제하는 것
- 한번 클론을 적용한 컴퓨터를 제외하고 다른 컴퓨터일 경우 클론을 사용



```bash
$ git add .

$ git commit -m "second commit"

$ git log --oneline

$ git push origin master

# 로컬(강의실), git-class에서 github, git-remote에 푸쉬
```



#### 6. 원격 저장소 변경 사항 받아오기(pull)

```bash
# 로컬(집)에서
$ git pull

# github, git-remote에서 집(로컬), git-home에 내려받음
```

- 한번 클론을 이용해 저장했다면 pull을 이용
- 원격 저장소가 바뀌었으면 반드시 pull 먼저 하고 사용할 것!!
- Github에서 수정하지말것!!!

```bash
# 로컬(집)에서 수정 후
$ git init

$ git add.

$ git commit -m "third commit"

$ git push origin master

# 로컬(집), git-home에서 github, git-remote에 푸쉬
```

- pull을 하지 않고 conflict 발생 할 경우

  - github commit과 로컬 commit이 겹치기때문에 할려고 했던 작업으로 하고  다시 commit을 한다

    ```bash
    # 탈출 명령어
    esc :wq enter
    ```

  - commit은 github commit, 로컬 commit, merge commit이 저장된다.
  - 무조건 pull 먼저할 것!!

