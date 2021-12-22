# Git 특강 2일차

#### 원격 저장소 연결

```bash
$ git remote add origin https://github.com/ydo1619/TIL.git
```



#### 원격 저장소 연결 여부 확인

```bash
$ git remote -v

origin  https://github.com/ydo1619/TIL.git (fetch)
origin  https://github.com/ydo1619/TIL.git (push) 
```



#### Github에 파일 업로드

```bash
# 현재 상태 확인
$ git status

$ git add .

$ git commit -m "Upload day2"

# 커밋 확인
$ git log --online

$ git push -u origin master
# 이후에는 $ git push 라고만 작성해도 push 가능
```



#### 수정 후 업로드

```bash
$ git add .

$ git status

$ git commit -m "Update day2"   # 로컬에 저장

$ git push 						# Github에 저장
```

