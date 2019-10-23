---
title: "자주쓰는 git 명령어"
layout: post
---



### git 명령어

>git status --> 수정 파일 확인  

>git add (-A | file) -A 은 수정된 파일 전부 add, 선택하면 선택한 file만 add

>git commit -m "할말" add한 파일을 commit

>git push origin (브랜치 이름) 브랜치를 git에 push함.

>git reset --hard HEAD (현재 브랜치의 초기상태로 되돌림 , 모든 코드 사라짐)

>git checkout next --> next branch로 branch 변경함  

>git pull --> 현재 branch에서 git에 업데이트된 정보를 다운받음

>git rebase master --> 마스터 branch를 현재 내 branch에 rebase함

>git rebase --abort --> rebase 전으로 되돌림

>git checkout -b 브랜치이름 -- 브랜치 생성 (현재 위치한 브렌치에서 생성됨)

>git branch -d 브랜치이름 -- 브랜치 삭제

>git reset --soft HEAD~1 수정한 데이터 존재하게 전 커밋으로 리셋

>git reset --hard HEAD~1 수정한 데이터 존재하지 않게 전 커밋으로 리셋

>git checkout -- src/hello.c 특정 파일 작업내용을 되돌림