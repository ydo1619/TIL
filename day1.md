# CLI

1. CLI 와 GUI
   - CLI : 터미널을 통해 사용자와 컴퓨터가 상호작용하는 방식
     - 구현방법 : mkdir new
   - GUI : 그래픽을 통해 사용자와 컴퓨터가 상호작용하는 방식
     - 구현방법 : 마우스 우클릭 -> 새로 만들기 ->  폴더 -> new 작성
2. 루트 디렉토리와 홈 디렉토리
   - 루트 디렉토리 : (Root Directory, / )
     - 모든 파일과 폴더를 담고있는 최상의 폴더
     - Windows 경우 보통 C 드라이브 의미
   - 홈 디렉토리 : (Home Directory, ~)
     - Tilde(틸드)라고도 부르며, 현재 로그인된 사용자의 홈 폴더를 의미
     - Windows의 경우 C:/사용자(Users)/현재 사용자 계정을 의미
3. 절대 경로와 상대 경로
   - 절대 경로 : 루트 디렉토리부터 목적 지점까지 거치는 모든 경로를 전부 작성한 것
     - 윈도우 바탕 화면의 절대 경로 `C:/Users/yd16/Desktop`
   - 상대 경로 : 현재 작업하고 있는 디렉토리를 기준으로 계산된 상대적 위치를 작성한 것
     - 현재 작업하고 있는 디렉토리가 `C:/Users` 라고 한다면
     - 윈도우 바탕 화면으로의 상대 경로는 `yd16/Desktop`
     - 간결해서 좋지만, 현재 작업하고 있는 디렉토리가 변경 되면 상대 경로도 변경됨
     - `./` : 현재 작업하고 있는 폴더를 의미
     - `../` : 현재 작업하고 있는 폴더의 부모 폴더를 의미

4. 터미널 명령어

- touch : 파일을 생성

  - ```bash
    $ touch text.txt

- mkdir : 새 폴더를 생성

  - ```bash
    $ mkdir folder
    $ mkdir 'happy hacking'
    ```

- ls : list segments 현재 작업 중인 디렉토리의 폴더/파일 목록을 보여주는 명령어

  - `-a` : all 옵션. 숨김 파일까지 모두 보여줌

  - `-l` : long 옵션. 용량, 수정 날짜 등 파일 정보를 자세히 보여줌

  - ```bash
    # 기본 사용
    $ ls 
    
    # all 옵션
    $ ls -a
    
    # all, long 옵션 함께 적용
    $ ls -a -l
    
    # 여러 옵션 축약 가능
    $ ls -al
    ```

- mv : move 폴더/파일을 다른 폴더 내로 이동 하거나 이름을 변경하는 명령어

  - 단, 다른 폴더로 이동할 때는 작성한 폴더가 반드시 있어야 함. 없으면 이름이 바뀜

  - ```bash
    # text.txt를 folder 폴더 안에 넣을 때
    $ mv text.txt folder
    
    # text1.txt의 이름을 text2.txt로 바꿀 때
    $ mv text1.txt text2.txt
    ```

- cd : change directory 현재 작업 중인 디렉토리를 변경하는 명령어

  - `cd ~` 를 입력하면 홈 디렉토리로 이동. (단순히 cd 라고만 입력해도 동일)

  - `cd ..` 를 입력하면 부모 디렉토리로 이동. (위로 가기)

  - `cd -` 를 입력하면 바로 전 디렉토리로 이동. (뒤로 가기)

  - ```bash
    # 현재 작업 중인 디렉토리에 있는 folder 폴더로 이동
    $ cd folder
    
    # 절대 경로를 통한 디렉토리 변경
    $ cd C:/Users/kyle/Desktop
    
    # 상대 경로를 통한 디렉토리 변경
    $ cd ../parent/child
    ```

- rm : remove 폴더/파일 지우는 명령어

  - GUI와 달리 휴지통으로 이동하지 않고, 바로 완전 삭제
  - `*(asterisk, wildcard)`를 사용해서 `rm *.txt` 라고 입력하면 txt 파일 전체를 다 지움
  - `-r` : recursive 옵션. 폴더를 지울 때 사용

  - ```bash
    $ rm test.txt
    $ rm -r folder
    ```

- start : 폴더/파일을 여는 명령어

  - ```bash
    # Windows
    $ start test.txt
    ```





# 마크다운

제목

# 제목 1

## 제목 2

### 제목 3

#### 제목 4

##### 제목5

###### 제목6



목록

순서가 없는 목록

- 목록 1
- 목록 2
- 목록 3
- 과일
  - 수박
  - 참외

-, *. + ->  순서가 없는 목록





순서가 있는 목록

1. 목록1
2. 목록2
   1. 목록2-1
   2. 목록2-2

---



강조(스타일링)

1. 기울임(이탤릭체): *글자* _글자_
2. 굵게(볼드체): **글자**
3. 취소선: ~~글자~~

---

코드 

인라인 코드(=한줄)

파이썬에는 `print("Hello World!")` 라고 쓸 수 있습니다.



블록 코드(=여러줄)

```python
for i in range(10):
	print(i)
```

---

수평선

-,*,_ 3번 연속 작성

---

***

___



---

표(table)

| 동물   | 다리 개수 | 종     |
| ------ | --------- | ------ |
| 사자   | 4개       | 포유류 |
| 원숭이 | 2개       | 포유류 |
| 앵무새 | 2개       | 조류   |
|        |           |        |
|        |           |        |





문자열 이스케이프

\'print()\'

\-



# Git

1. Git을 이용한 버전관리 작성자 등록 (딱 1번만)

   - git config --global user.name dongouk

   - git config --global user.email ydo1619@naver.com
2. 어떤 폴더를 Git으로 버전관리 하겠다.
   - git init
3.  Working Directory -> Staging Area
   - git add a.txt
4. Staging Area -> Commits (버전)
   - git commit -m "first commit"
5. 현재 Git이 관리하는 파일의 상태
   - git status
6. 버전 로그 보여줌 (커밋 로그 보여줌)
   - git log
   - git log -p (커밋의 변경내역)
   - git log --oneline (한 줄로 출력)



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









