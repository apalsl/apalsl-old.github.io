---
title: "Java File 탐색 및 삭제"
layout: post
comments : true
---


Java에서 특정 위치의 파일 목록을 탐색

```java
    @Test
    public void search(){
        String path = "C:\\Users\\windows\\Desktop\\fileTest/";

        for(File info : new File(path).listFiles()) {
            System.out.println(info.getName());
        }
    }
```

만약 파일의 위치와 이름을 정확하게 알고 있다고 가정하면
```java
File file = new File("C:\\Users\\file.txt");
```


삭제는 다음과 같이 파일을 찾고 원하는 파일일때 삭제하면 끝
```java
  @Test
    public void delete(){
        String path = "C:\\Users\\windows\\Desktop\\fileTest/";

        for(File info : new File(path).listFiles()) {
            System.out.println(info.getName());
        }

        for(File info : new File(path).listFiles()) {

            if(info.getName().equals("test5.txt"))  {
                info.delete();
            }
        }
    }
```
