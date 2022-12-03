# Git 환경설정
```
dski2@BOOK-6MKSS57FS2 MINGW64 ~/OneDrive/Desktop (master)
$ git config --global user.name "eunyoung"

dski2@BOOK-6MKSS57FS2 MINGW64 ~/OneDrive/Desktop (master)
$ git config --global user.email "dski2335@gmail.com"

dski2@BOOK-6MKSS57FS2 MINGW64 ~/OneDrive/Desktop (master)
$ git config --global core.quotepath false
```


<details>
<summary><h2>Git 기본명령어</h2></summary>
<div markdown="1">

## Git init(저장소 만들기)
1. ```sample```디렉토리 생성 후 이동
```
dski2@BOOK-6MKSS57FS2 MINGW64 ~ (master)
$ mkdir sample  // 디렉토리 생성

dski2@BOOK-6MKSS57FS2 MINGW64 ~ (master)
$ cd sample // 이동

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ pwd
/c/Users/dski2/sample
```
2. 파일 생성 후 글자 추가하여 저장소 만들기
```
사용 구문 : echo "문장" >> 파일 
→ 파일에 글자 추가
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ echo "테스트1" >> test1

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ echo "테스트2" >> test2

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git init
Initialized empty Git repository in C:/Users/dski2/sample/.git/
→ git 저장소 생성

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ ls -al
total 18
drwxr-xr-x 1 dski2 197609  0 Dec  3 16:40 ./
drwxr-xr-x 1 dski2 197609  0 Dec  3 16:36 ../
drwxr-xr-x 1 dski2 197609  0 Dec  3 16:40 .git/     → 결과 
-rw-r--r-- 1 dski2 197609 11 Dec  3 16:40 test1
-rw-r--r-- 1 dski2 197609 11 Dec  3 16:39 test2

** .git 디렉토리
버전 관리할 때 여러가지 정보들이 생성되는데 .git 디렉토리에 저장된다.
즉, 버전 정보를 저장하는 디렉토리이다.
```

## Git status & add(현재 상태 확인 및 추적)

1. 디렉토리에 파일 생성
```
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ cat f1.txt
source : 1
```
![image](https://user-images.githubusercontent.com/103404357/205430753-e08bc821-02c3-4258-b5be-fc9de045af78.png)

2. 파일 내용 확인
```
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ cat f1.txt
source : 1

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ cat test1
테스트1
```

3. 추적 상태 확인
```
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git status
On branch master

No commits yet

Untracked files:  → 추적되고 있지 않다! 즉, 버전 관리하고 있지 않다.
  (use "git add <file>..." to include in what will be committed)
        f1.txt
        test1
        test2

nothing added to commit but untracked files present (use "git add" to track)

```

4. ```add```를 통해 버전 관리 하라고 명령하기
```
→ 버전 관리 명령 실행
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git add f1.txt test1 test2 
warning: in the working copy of 'f1.txt', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'test1', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'test2', LF will be replaced by CRLF the next time Git touches it

→ 버전 관리 실행
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   f1.txt
        new file:   test1
        new file:   test2


** 왜 add를 통해 버전 관리를 실행해야 하는가?
- 프로젝트 진행시 임시 파일인 경우 버전 관리에서 배제하기 위해 관리하기 위한 파일이 무엇인지 명확하게 알려주기 위해서 사용해야한다.
```

</div>
</details>
