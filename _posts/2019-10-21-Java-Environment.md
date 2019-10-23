---
title: "Linux VSCODE 자바 컴파일"
layout: post
---

###  VSCODE에서 JAVA 개발환경 구성하기

VSCODE에서 SSH로 리눅스를 접근, JAVA 개발환경 설정하기 



Linux에서 Openjdk를 설치한다.

 jdk 리스트 확인

yum list java*jdk-devel 

 jdk 설치

sudo yum install -y java-1.8.0-openjdk-devel.x86_64



vscode에서 필요한 Java 플러그인

![4](/img/java_plugin.PNG)
   
직접 설치하지 않아도 자바에 관련된 플러그인이 없을때 .java 파일을 만들면 vscode에서 알아서 안내해줌, 만약 안내창이 뜨지 않거나 설치가 안되면 서버에 위 사진과 같은 extension을 전부 설치하면 된다.



![5](/img/java_helloworld.PNG)

extensions 설치가 끝나면 다음과 같이 자바 코드를 짰을때 run과 Debug가 생김. (이것때문에 했다)


### 가장 중요한 한 줄 지우기 단축키

Ctrl + Shift + K

or 

Cmd +  Shift + K