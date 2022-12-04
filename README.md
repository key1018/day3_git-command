# Git 환경설정
```
dski2@BOOK-6MKSS57FS2 MINGW64 ~/OneDrive/Desktop (master)
$ git config --global user.name "eunyoung"

dski2@BOOK-6MKSS57FS2 MINGW64 ~/OneDrive/Desktop (master)
$ git config --global user.email "dski2335@gmail.com"

dski2@BOOK-6MKSS57FS2 MINGW64 ~/OneDrive/Desktop (master)
$ git config --global core.quotepath false

✅ 버전 관리를 누가 했는지 알 수 있도록 설정하는 것.
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
✅ 파일에 글자 추가
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ echo "테스트1" >> test1

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ echo "테스트2" >> test2

✅ git 저장소 생성
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git init
Initialized empty Git repository in C:/Users/dski2/sample/.git/

✅ 결과 
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ ls -al
total 18
drwxr-xr-x 1 dski2 197609  0 Dec  3 16:40 ./
drwxr-xr-x 1 dski2 197609  0 Dec  3 16:36 ../
drwxr-xr-x 1 dski2 197609  0 Dec  3 16:40 .git/    
-rw-r--r-- 1 dski2 197609 11 Dec  3 16:40 test1
-rw-r--r-- 1 dski2 197609 11 Dec  3 16:39 test2

💡 .git 디렉토리
→ 버전 관리할 때 여러가지 정보들이 생성되는데 .git 디렉토리에 저장된다.
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
✅ 버전 관리 명령 실행
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git add f1.txt test1 test2 
warning: in the working copy of 'f1.txt', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'test1', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'test2', LF will be replaced by CRLF the next time Git touches it

✅ 버전 관리 실행
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   f1.txt
        new file:   test1
        new file:   test2


💡 왜 add를 통해 버전 관리를 실행해야 하는가?
 → 프로젝트 진행시 임시 파일인 경우 버전 관리에서 배제하기 위해 관리하기 위한 파일이 무엇인지 명확하게 알려주기 위해서 사용해야한다.
```
## Git commit (현재 상태 저장, 버전 만들기)
버전이란? <br>
➡️ 의미있는 변화를 의미한다. 즉, 작업이 완성된 상태를 말한다. <br>
사용 구문 : git commit [-m <msg>] <br>

1. 수정없이 파일을 commit할 때
```
✅ commit 실행
이 파일이 왜 변경 되었는지에 대한 현재 버전의 정보를 적어야됨
1    → 버전1 이라는 정보
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch master
#
# Initial commit
#
# Changes to be committed:
#       new file:   f1.txt
#       new file:   test1
#       new file:   test2
#

✅ commit 완료
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git commit
[master (root-commit) 6cbe8fe] 1
 3 files changed, 3 insertions(+)
 create mode 100644 f1.txt
 create mode 100644 test1
 create mode 100644 test2
 
✅ 버전이 잘 생성되었는지 확인
 dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git log
commit 6cbe8fe207615fb070fc429d5c61de3b98a458e6 (HEAD -> master)
Author: eunyoung <dski2335@gmail.com> → 누가 버전을 만들었는지
Date:   Sun Dec 4 02:40:57 2022 +0900 → 언제 버전을 만들었는지

    1     → 버전1
```

2. 수정한 후 commit할 때
```
✅ 파일 수정
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ vim test1

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   test1    → 수정됐다고 뜸

✅ add를 통해 버전 관리하라고 재명령하기
왜? git에서 새로운 파일이 생긴 경우나 파일이 이미 버전 관리가 되어있는 파일이 수정되어 버전을 재생성 할 때도 해야하기 때문이다.
방대한 양을 commit해야할 때 선택적으로 파일을 커밋할 수 있다.
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git add test1

✅ 수정한 파일 버전 관리 명령 후 commit
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git commit -m "v2"

✅ 이력 확인
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git log
commit 8b47153c2f281530ef239c278ad8dde800275ecb (HEAD -> master)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:58:01 2022 +0900

    v2

commit 6cbe8fe207615fb070fc429d5c61de3b98a458e6
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:40:57 2022 +0900

    1
```
```
💡 팁! <br>
1. echo "[글자]" >> [파일]: 파일에 글자 추가
2. 
# -m : vi에서 별도의 메세지를 작성하지 않고 인라인 형식으로 바로 커밋 메세지를 작성하기 위한 옵션
# -a : 별도의 add 명령어를 사용하지 않고 수정된 파일에 대해 add를 수행하는 옵션
# -am : a 옵션과 m 옵션을 합쳐서 사용하는 방법

$ git commit -am [버전]
단, -a 옵션은 새로생성된 파일은 안먹힌다.
따라서 새로만든 파일을 커밋할 경우 git add를 따로 해줘야 한다.
```

## Git log & diff (변경 사항 확인하기)
### log
➡️ 커밋 내역을 확인해보고 싶을 때 사용하는 명령어이다. <br>
이를 이용해서 이전 단계로 되돌리거나 버전관리를 할 수 있다. <br>

| git log | 명령어 예시 설명 | 
----- | ----- |
| git log -p | 각 commit사이의 소스상의 차이점을 보고 싶을 때 |
| git log	| HEAD와 관련된 commit들이 자세하게 나옴 |
| git log --oneline	| 간단히 commit 해시와 제목만 보고 싶을 때 |
| git log --oneline --graph --decorate | HEAD와 관련된 commit들을 조금 더 자세히 보고 싶을 때 |
| git log --oneline --graph --all --decorate | 모든 branch들을 보고 싶을 때 사용하는 명령어 |
| git log --oneline -n7 |	내 branch의 최신 commit을 7개만 보고 싶을 때 사용 |

### diff
➡️ 커밋된 최근 버전과 작업 폴더의 수정 파일 사이의 차이를 출력할 때 사용하는 명령어이다. <br>
작업 트리에 있는 파일과 스테이지에 있는 파일을 비교하거나, 스테이지에 있는 파일과 저장소에 있는 최신 커밋을 비교해서 <br>
수정한 파일을 커밋하기 전에 최종적으로 검토할 수 있다.
```
# commit된 파일상태와 현재 수정중인 상태 비교
$ git diff
 
# commit된 파일상태와 add된 파일 상태 비교
$ git diff --staged
 
# commit간의 상태 비교하기 - commit hash 이용
$ git diff [비교할commit해쉬1] [비교할commit해쉬2]
$ git diff 048171 0c747d
 
# commit간의 상태 비교하기 - HEAD 이용
$ git diff HEAD HEAD^
# -- 가장 최근의 커밋과 그 전의 커밋을 비교한다
 
# branch간의 상태 비교하기 - HEAD 이용
$ git diff [비교할branch1] [비교할branch2]
$ git diff feature/test origin/master
# -- local의 feature/test브런치와 remote의 master branch 비교

✅ 실전
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git diff
warning: in the working copy of 'test1', LF will be replaced by CRLF the next time Git touches it
diff --git a/test1 b/test1
index 6a51240..f8c1e5c 100644
--- a/test1
+++ b/test1
@@ -1,2 +1 @@
-테스트다시진행  // 수정 전
 orange         // 수정 후

```

## Git reset (이전 상태로 - 이력 제거)
➡️ 특정 커밋까지 이력을 초기화하는 명령어이다. <br>
바로 전, 또는 n번 전까지 작업했던 내용을 취소할 수 있다. <br>
이력이 지워지기 때문에 주의해야 한다. <br>
```
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git log
commit 376ade1a85e811c82cbc9444a0ccc74d04a07423 (HEAD -> master)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 04:44:28 2022 +0900

    v5

commit 7ba374004eb4216833e19b803bebff8234d54612
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 03:08:30 2022 +0900

    delete

commit 9dfeff433cc31a43c0b6eea6edc00fd158c7316d     → 커밋 아이디
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 03:06:41 2022 +0900

    v4

commit eb45826efa9389706217efbd5932c8b04e7c7f49
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 03:05:23 2022 +0900

    v3

commit 8b47153c2f281530ef239c278ad8dde800275ecb
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:58:01 2022 +0900

    v2

    
✅ v5와 delete를 삭제하고 v4로 돌아가고 싶은 경우 예) 9dfeff433cc31a43c0b6eea6edc00fd158c7316d
사용 구문 : git reset {v2 커밋 아이디} --hard
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git reset 9dfeff433cc31a43c0b6eea6edc00fd158c7316d --hard

✅ v4버전이 최신인 것을 확인
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git log
commit 9dfeff433cc31a43c0b6eea6edc00fd158c7316d (HEAD -> master)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 03:06:41 2022 +0900

    v4

commit eb45826efa9389706217efbd5932c8b04e7c7f49
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 03:05:23 2022 +0900

    v3

commit 8b47153c2f281530ef239c278ad8dde800275ecb
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:58:01 2022 +0900

    v2
```

## Git revert (이전 상태로 - 이력 유지)
➡️ 특정 커밋을 취소하는 새로운 커밋을 만드는 명령어이다. <br>
일반적으로 특정 버전을 배포했는데 문제가 생기면 문제가 생긴 커밋을 revert한다. (빠른 조치/롤백) <br>
다시 원복한 상태로 작업을 이어서 하고 해당 문제를 수정하면 다시 커밋하는 방식을 사용합니다. <br>
```
사용 구문 git revert {v3 커밋 아이디}

✅ 수정해서 commit
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ echo revert_test >> test1

✅ 추적 상태 확인
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   test1

no changes added to commit (use "git add" and/or "git commit -a")

✅ add와 commit 동시에 진행
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git commit -am v5
warning: in the working copy of 'test1', LF will be replaced by CRLF the next time Git touches it
[master 27aa932] v5
 1 file changed, 1 insertion(+)

✅ v5의 버전이 저장된 것을 확인
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git log
commit 27aa9321282fddf67c5b42522f9584d7aaa7b55d (HEAD -> master)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 05:07:25 2022 +0900

    v5

✅ v5 버전 revert하기
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git revert 27aa9321282fddf67c5b42522f9584d7aaa7b55d
[master b86a649] Revert "v5"
 1 file changed, 1 deletion(-)


✅ v5가 revert된 것 확인
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git log
commit 27aa9321282fddf67c5b42522f9584d7aaa7b55d (HEAD -> master)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 05:07:25 2022 +0900

    v5

commit 9dfeff433cc31a43c0b6eea6edc00fd158c7316d
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 03:06:41 2022 +0900

    v4

commit eb45826efa9389706217efbd5932c8b04e7c7f49
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 03:05:23 2022 +0900

    v3

commit 8b47153c2f281530ef239c278ad8dde800275ecb
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:58:01 2022 +0900

    v2
    
✅ v5 커밋 취소
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git log
commit b86a64946cd5d159997adbcfd4545759cd27a4a1 (HEAD -> master)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 05:09:49 2022 +0900

    Revert "v5"

    This reverts commit 27aa9321282fddf67c5b42522f9584d7aaa7b55d.

commit 27aa9321282fddf67c5b42522f9584d7aaa7b55d
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 05:07:25 2022 +0900

    v5

commit 9dfeff433cc31a43c0b6eea6edc00fd158c7316d
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 03:06:41 2022 +0900

    v4

commit eb45826efa9389706217efbd5932c8b04e7c7f49
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 03:05:23 2022 +0900

    v3

commit 8b47153c2f281530ef239c278ad8dde800275ecb
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:58:01 2022 +0900

    v2
```

</div>
</details>
  
<details>
<summary><h2>Git Branch</h2></summary>
<div markdown="1">

# branch란?
➡️ 동시에 다양한 작업을 할 수 있게 만들어 주는 기능으로 각자 독립적인 작업 영역(저장소) 안에서 마음대로 소스코드를 변경할 수 있다. <br>
브래치는 독립적으로 어떤 작업을 진행하기 위한 개념으로, 필요에 의해 만들어지는 각각의 브랜치는 다른 브랜치의 영향을 받지 않기 때문에 여러 작업을 동시에 진행할 수 있게 된다.
  
## git branch / swich -c|-C (브랜치 생성)
```
사용 구문1 : $ git branch <브랜치이름>
사용 구문2 : $ git switch (-c|-C) <브랜치이름>
  
✅ 사용 구문1
  
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git branch newbranch1

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git branch
* master    
  newbranch1    → 새로 생성된 브랜치

✅ 사용 구문2

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git switch -c newbranch2
Switched to a new branch 'newbranch2'

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch2)
$ git branch
  master
  newbranch1
* newbranch2    → 브랜치를 생성하면서 이동
```
  
## git chechout / switch (브랜치 변경)
```
사용 구문1 : $ git branch <브랜치이름>
사용 구문2 : $ git switch (-c|-C) <브랜치이름>
  
✅ 사용 구문1
  
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git checkout newbranch1
Switched to branch 'newbranch1'

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch1)
→ newbranch1로 이동
  
✅ 사용 구문2
  
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch1)
$ git switch newbranch2
Switched to branch 'newbranch2'

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch2)
→ newbranch2로 이동
 
💡 branch를 생성하면 생성된 브랜치는 현재 내가 속해있는 브랜치의 상태를 그대로 복사한 후 생성된다.
```
  
## git update (브랜치 수정)
```
✅ newbranch2에서 파일 수정 후 커밋
  
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch2)
$ vim f1.txt

→ 파일 수정
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch2)
$ git status
On branch newbranch2
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   f1.txt

no changes added to commit (use "git add" and/or "git commit -a")

→ 버전 관리 권한 생성
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch2)
$ git add f1.txt

→ 커밋 
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch2)
$ git commit -m v3

✅ newbranch2 log 확인
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch2)
$ git log
commit 35c004674486a956b484f56ea506a5f7bf888984 (HEAD -> newbranch2)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 19:55:06 2022 +0900

    v3      → 새로운 커밋 생성

commit 8b47153c2f281530ef239c278ad8dde800275ecb (newbranch1, master)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:58:01 2022 +0900

    v2

commit 238e3548d9f81faab53475560458090b0467c96e
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:54:44 2022 +0900

    2

commit 6cbe8fe207615fb070fc429d5c61de3b98a458e6
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:40:57 2022 +0900

    1
  
✅ newbranch1 log 확인
→ 새로운 커밋 생성 x
  
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch1)
$ git log
commit 8b47153c2f281530ef239c278ad8dde800275ecb (HEAD -> newbranch1, master)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:58:01 2022 +0900

    v2

commit 238e3548d9f81faab53475560458090b0467c96e
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:54:44 2022 +0900

    2

commit 6cbe8fe207615fb070fc429d5c61de3b98a458e6
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:40:57 2022 +0900

    1

💡 어느 브랜치에 속해있냐에 따라서 내용이 와전히 달라진다!
```

## git merge (브랜치 병합)
  
```
# 지정한 branch의 commit들을 -> 현재 branch 및 워킹 트리에 반영
# <브랜치이름>에 merge하는게 아닌, 현재 브랜치 이곳에 <브랜치이름>을 merge하는 것이다. 
  
사용 구문 : git merge <브랜치이름>
  
→ newbranch2의 내용을 newbranch1로 옮기기

✅ newbranch1에서 합병하기 때문에 해당 브래치로 이동
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch2)
$ git switch newbranch1
Switched to branch 'newbranch1'
  
✅ 합병
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch1)
$ git merge newbranch2
Updating 8b47153..35c0046
Fast-forward
 f1.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

✅ newbranch1의 log확인
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch1)
$ git log
commit 35c004674486a956b484f56ea506a5f7bf888984 (HEAD -> newbranch1, newbranch2)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 19:55:06 2022 +0900

    v3

commit 8b47153c2f281530ef239c278ad8dde800275ecb (master)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:58:01 2022 +0900

    v2

commit 238e3548d9f81faab53475560458090b0467c96e
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:54:44 2022 +0900

    2

commit 6cbe8fe207615fb070fc429d5c61de3b98a458e6
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:40:57 2022 +0900

    1

```

## git branch -d (브랜치 삭제)
```
사용 구문 : git branch -d 삭제할 브랜치명  

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch1)
$ git branch -d newbranch2
Deleted branch newbranch2 (was 35c0046).

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch1)
$ git branch
  master
* newbranch1
```
  
## conflict 충돌 해결
  
### 1. 다른 이름의 파일인 경우
```
✅ master에서 새로운 수정 사항 생성

→ master.txt 파일 생성
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ vim master.txt

→ 버전 관리 실행 후 커밋
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git add master.txt
warning: in the working copy of 'master.txt', LF will be replaced by CRLF the next time Git touches it

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git commit -m v5
[master aeeb96a] v5
 1 file changed, 1 insertion(+)
 create mode 100644 master.txt

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git log
commit aeeb96ab5b45e078f7bf54233d9d683e00783092 (HEAD -> master)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 20:43:13 2022 +0900

    v5

commit 8b47153c2f281530ef239c278ad8dde800275ecb
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:58:01 2022 +0900

    v2

commit 238e3548d9f81faab53475560458090b0467c96e
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:54:44 2022 +0900

    2

commit 6cbe8fe207615fb070fc429d5c61de3b98a458e6
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:40:57 2022 +0900

    1

  
✅ newbranch1에서 새로운 수정 사항 생성
  
→ exp.txt 파일 생성
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch1)
$ vim exp.txt

→ 버전 관리 실행 후 커밋
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch1)
$ git add exp.txt
warning: in the working copy of 'exp.txt', LF will be replaced by CRLF the next time Git touches it

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch1)
$ git commit -m exp_test
[newbranch1 8b549b8] exp_test
 1 file changed, 1 insertion(+)
 create mode 100644 exp.txt

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch1)
$ git log
commit 8b549b8815410fd924ab355fc09fb025348a16b2 (HEAD -> newbranch1)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 20:44:55 2022 +0900

    exp_test

commit 35c004674486a956b484f56ea506a5f7bf888984
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 19:55:06 2022 +0900

    v3

commit 8b47153c2f281530ef239c278ad8dde800275ecb
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:58:01 2022 +0900

    v2

commit 238e3548d9f81faab53475560458090b0467c96e
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:54:44 2022 +0900

    2

commit 6cbe8fe207615fb070fc429d5c61de3b98a458e6
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:40:57 2022 +0900

    1

✅ amster와 newbranch1의 log 비교
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git log --branches
commit 8b549b8815410fd924ab355fc09fb025348a16b2 (newbranch1)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 20:44:55 2022 +0900

    exp_test        → newbranch1에서 커밋
  
commit aeeb96ab5b45e078f7bf54233d9d683e00783092 (HEAD -> master)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 20:43:13 2022 +0900

    v5              → master에서 커밋

commit 35c004674486a956b484f56ea506a5f7bf888984
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 19:55:06 2022 +0900

    v3

commit 8b47153c2f281530ef239c278ad8dde800275ecb
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:58:01 2022 +0900

    v2

commit 238e3548d9f81faab53475560458090b0467c96e
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:54:44 2022 +0900

    2

commit 6cbe8fe207615fb070fc429d5c61de3b98a458e6
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 02:40:57 2022 +0900

    1 

✅ 합병

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git merge newbranch1
```
→ 충돌 발생 <br>  
![image](https://user-images.githubusercontent.com/103404357/205488880-fa10450d-6afe-4143-ba74-6cb7082d703a.png) <br>
  
→ 합병 완료 <br>
왜? 파일이 다르면 자동으로 합병됨 <br>
![image](https://user-images.githubusercontent.com/103404357/205489039-ab763be3-b95a-4fd4-bd70-86b5a331c6ca.png) <br>
  
→ master에 exp.txt 생성 완료 <br>
![image](https://user-images.githubusercontent.com/103404357/205489069-38fb8055-20c2-49a4-a5e7-ce2312831c02.png) <br>

### 2. 같은 이름의 파일인 경우
```
  
✅ master에서 common.txt파일 수정
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ cat common.txt
function a() {

}

function b() {        → newbranch1과 다름

}


✅ newbranch1에서 common.txt파일 수정
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (newbranch1)
$ cat common.txt
function a() {

}
function c() {        → master과 다름

}

 
✅ 합병
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git merge newbranch1

✅ 충돌 발생
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git merge newbranch1
Auto-merging common.txt
CONFLICT (content): Merge conflict in common.txt
Automatic merge failed; fix conflicts and then commit the result.

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master|MERGING)
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   common.txt

no changes added to commit (use "git add" and/or "git commit -a")
```  
→ 오류 발생 <br>
![image](https://user-images.githubusercontent.com/103404357/205489738-f2242067-4e48-4309-8f80-e61f540b663c.png) <br>

```
✅ 수정
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master|MERGING)
$ git add common.txt

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master|MERGING)
$ git status
On branch master
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:
        modified:   common.txt
```
→ 오류 수정 후 <br>
![image](https://user-images.githubusercontent.com/103404357/205489929-48ba57d1-63a3-4196-b33d-ba502cd80866.png) <br>
  
```
✅ 완전히 합병된 것을 확인
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ cat common.txt
function a() {

}
function b() {

}
function c() {

}

```

</div>
</details>

<details>
<summary><h2>Git 원격저장소</h2></summary>
<div markdown="1">
  
## 저장소 생성하기
![image](https://user-images.githubusercontent.com/103404357/205493851-d0da6357-82a7-41c2-a93c-5a2cd1dcb79d.png) <br>
  
## git remote (Remote Repository 연결)
➡️ git remote 명령으로 현재 프로젝트에 등록된 리모트 저장소를 확인할 수 있다. <br>
이 명령은 리모트 저장소의 단축 이름을 지어준다. <br>
URL은 제일 상단 부에서 확인 가능하고, 클립보드에 복사하도록 제공 하기도 한다. <br>
  
![image](https://user-images.githubusercontent.com/103404357/205493866-d82e12dc-ee37-4c15-b0f3-1d8490c3840b.png) <br>
→ 해당 주소는 레파지토리의 고유 주소이다. <br>
 
```
사용 구문 : $ git remote add origin URL주소
# git remote add <remote repo 이름> <repo url>
# https://github.com/깃헙계정/리포지터리명.git 
# url를 origin이라고 이름을 붙여 추가하겠다는 의미
 
# url가져오기
$ git remote get-url origin

✅ 현재 원격저장소에 연결시킨다.
  
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/local (master)
$ git remote add origin https://github.com/key1018/sample.git

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/local (master)
$ git remote
origin    → 원격저장소의 이름 (주로 메인이 되는 저장소) 

💡 옵션
# 옵션 종류 보기
$ git remote --help
 
# 추가한 원격저장소의 목록 확인 
$ git remote
$ git remote -v # 상세히
 
# 특정 원격 저장소의 정보를 확인할 수 있다.
$ git remote show 이름
 
# 원격저장소 이름 변경
$ git remote rename 기존이름 변경할이름
 
# 원격저장소를 제거
$ git remote rm 이름
  
💡 깃은 여러개의 저장소를 로컬저장소에 저장할 수 있다.
```
  
## git push (원격 저장소 저장)
➡️ 현재 branch에서 새로 생성한 commit들을 원격 저장소에 업로드 <br>
로컬 컴퓨터에서 작업하고 커밋을 깃허브에서 온라인으로도 볼 수 있다. 
  
```
사용 구문 : $ git push -u origin master
# origin : 원격주소 / master : 브랜치
# 영어문법 4형식 -> origin에 master를 push하라

✅ 처음으로 원격 저장소로 업로드
  
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/local (master)
$ git push -u origin master       → 업로드하는 명령어
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 202 bytes | 202.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/key1018/sample.git
 * [new branch]      master -> master
branch 'master' set up to track 'origin/master'.
```

→ 업도르된 사진 <br>
![image](https://user-images.githubusercontent.com/103404357/205494563-5a437aa9-5b63-4251-a6ef-a3eac0999453.png) <br>

```
✅ 두 번째 업로드 실행
  
→ 깃 수정
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/local (master)
$ vim f1.txt

→ 버전 관리 권한 생성 및 커밋
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/local (master)
$ git commit -am 2
warning: in the working copy of 'f1.txt', LF will be replaced by CRLF the next time Git touches it
[master ed022c2] 2
 1 file changed, 2 insertions(+)

→ 바로 push 입력  
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/local (master)
$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Writing objects: 100% (3/3), 234 bytes | 234.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/key1018/sample.git
   79371dd..ed022c2  master -> master

💡 바로 push가 가능하다!
```
→ 업로드된 사진 <br>
![image](https://user-images.githubusercontent.com/103404357/205495702-c9e05be8-5cab-4522-ab6c-4ad0328843bf.png) <br>

## git clone (원격 저장소 복제)
➡️ 원격 저장소의 저장소를 내 local에서 이용할 수 있게 그대로 똑같이 복사해 가져온다. <br>
사용 구문 : $ git clone 레파지토리 주소 <br> <br>
  
✅ 주소 복사 <br>
![image](https://user-images.githubusercontent.com/103404357/205495948-332c3b2e-7b93-4b27-be67-44b40f44766f.png) <br>

```
✅ 깃 clone
. : 현재 디렉토리 라는 의미
  
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/gitt (master)
$ git clone https://github.com/key1018/sample.git .
Cloning into '.'...
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 6 (delta 0), reused 6 (delta 0), pack-reused 0
Receiving objects: 100% (6/6), done.

✅ 깃 clone 된 것을 확인
  
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/gitt (master)
$ ls -al
total 9
drwxr-xr-x 1 dski2 197609 0 Dec  4 23:23 ./
drwxr-xr-x 1 dski2 197609 0 Dec  4 23:22 ../
drwxr-xr-x 1 dski2 197609 0 Dec  4 23:23 .git/
-rw-r--r-- 1 dski2 197609 8 Dec  4 23:23 f1.txt

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/gitt (master)
$ git remote -v
origin  https://github.com/key1018/sample.git (fetch)
origin  https://github.com/key1018/sample.git (push)

```
  
## git pull (원격 저장소 내용 가져오기)
➡️ 원격 저장소에서 파일 내려받기 <br>
git pull = git fetch + git merge : 원격저장소 커밋과 동기화하고 커밋을 머지 시킨다. <br>
원격 저장소와 로컬 저장소의 상태를 같게 만들기 위해 원격 저장소의 소스를 가져오는 것이다. <br>
즉, 다른 사람들의 작업 변경사항을 클라이언트로 내려받기 한다고 보면 된다. <br>
```
# 원격 저장소의 변경사항을 워킹 트리에 반영
# git pull <remote> <branch>
사용 구문 : $ git pull origin master
  
✅ 깃 clone 반영(git_home, git_office 각각 따로 만들기)
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git clone https://github.com/key1018/sample.git git_home    → git_home
Cloning into 'git_home'...
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 9 (delta 0), reused 9 (delta 0), pack-reused 0
Receiving objects: 100% (9/9), done.

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git clone https://github.com/key1018/sample.git git_office    → git_office
Cloning into 'git_office'...
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 9 (delta 0), reused 9 (delta 0), pack-reused 0
Receiving objects: 100% (9/9), done.


✅ git_home에서 수정 후 push
  
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/git_home (master)
$ vim f1.txt

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/git_home (master)
$ git commit -am 3
[master 4a79cdb] 3
 1 file changed, 1 insertion(+), 1 deletion(-)

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/git_home (master)
$ git log
commit 4a79cdb677519a88101c87522dd06055c7083444 (HEAD -> master)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 23:42:05 2022 +0900

    3      → 새로 push한 사항

commit 708b033e4c9ea1f3fdd882eb3d1128474f8ed1a2 (origin/master, origin/HEAD)
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 23:34:27 2022 +0900

    add red

commit ed022c27893fb50e50ee39b1194c852bfded8030
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 23:15:20 2022 +0900

    2

commit 79371dd9f46df0de79082bfddbae0d468ed01b6e
Author: eunyoung <dski2335@gmail.com>
Date:   Sun Dec 4 22:27:12 2022 +0900

    1

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/git_home (master)
$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 264 bytes | 264.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/key1018/sample.git
   708b033..4a79cdb  master -> master
  
✅ git_office에서 push하기
  
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample/git_office (master)
$ git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 244 bytes | 16.00 KiB/s, done.
From https://github.com/key1018/sample
   708b033..4a79cdb  master     -> origin/master
Updating 708b033..4a79cdb
Fast-forward
 f1.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```
</div>
</details>
  
<details>
<summary><h2>GitHub Flow</h2></summary>
<div markdown="1">
  
## 브랜치 전략
➡️ 브랜치 전략이란 여러 개발자가 하나의 저장소를 사용하는 환경에서 저장소를 효과적으로 활용하기 위한 work-flow다. <br>
브랜치의 생성, 삭제, 병합 등 git의 유연한 구조를 활용해서, 각 개발자들의 혼란을 최대한 줄이며 다양한 방식으로 소스를 관리하는 역할을 한다. <br>
즉, 브랜치 생성에 규칙을 만들어서 협업을 유연하게 하는 방법론을 말한다. <br>
 
```
✅ rainbow 브랜치 생성
  
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (master)
$ git switch -c rainbow
Switched to a new branch 'rainbow'

→ red 파일 추가 후 커밋
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (rainbow)
$ touch red

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (rainbow)
$ echo "red" >> red

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (rainbow)
$ git add -A

dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (rainbow)
$ git commit -m "red"
[rainbow 0e10831] red
 4 files changed, 4 insertions(+), 1 deletion(-)
 create mode 160000 git_home
 create mode 160000 git_office
 create mode 100644 red

✅ 깃에 push하기
dski2@BOOK-6MKSS57FS2 MINGW64 ~/sample (rainbow)
$ git push origin rainbow
Enumerating objects: 45, done.
Counting objects: 100% (45/45), done.
Delta compression using up to 16 threads
Compressing objects: 100% (31/31), done.
Writing objects: 100% (45/45), 3.61 KiB | 923.00 KiB/s, done.
Total 45 (delta 13), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (13/13), done.
remote:
remote: Create a pull request for 'rainbow' on GitHub by visiting:
remote:      https://github.com/key1018/sample/pull/new/rainbow
remote:
To https://github.com/key1018/sample.git
 * [new branch]      rainbow -> rainbow

```
  
→ push 후 화면 <br>
![image](https://user-images.githubusercontent.com/103404357/205498896-9d443a1e-0114-4a2e-8194-bb374ef6598e.png) <br>
  
→ Compare & pull 버튼 생성 <br>
![image](https://user-images.githubusercontent.com/103404357/205498929-81c4ec5a-bb76-4d15-9900-2f985c0f9864.png) <br>
  
</div>
</details>


  
  
