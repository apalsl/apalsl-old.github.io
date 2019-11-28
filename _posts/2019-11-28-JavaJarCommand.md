---
title: "Java -jar 커맨드 명령어"
layout: post
comments : true
---


주로 java -jar -p를하여 로그를 찍어낸다던가 java -jar로 파일을 만들때 name을 받아버리면 좋다.  
또한 help 옵션을 이용하여 내가 받고 있는 커맨드 명렁어의 설명도 가능함.

코드는 다음과 같다. 사실 git에 소스로 넣으면 좋지만 무엇인가 결과물을 필요로 할때 작성할 예정(언젠가)


```java
import java.util.List;
import org.apache.commons.cli.CommandLine;
import org.apache.commons.cli.CommandLineParser;
import org.apache.commons.cli.HelpFormatter;
import org.apache.commons.cli.Options;
import org.apache.commons.cli.ParseException;
import org.apache.commons.cli.PosixParser;
public class Test {
public static void main(String[] args) {

//       try-catch가 필요함
  CommandLineParser clp = new PosixParser();
  Options opts = new Options();
  CommandLine cline = null;
 
        try{
         opts.addOption("p", "print", true, "Message.");
         opts.addOption("h", "help", false, "도움말을 출력합니다");
         opts.addOption("t" , "test" , true , "option test");      

//        addOption :
//       첫번째 p 옵션 : -p test  (test 를 출력 하는 것)
//       두번째 print 옵션 : --print data (data 를 출력 하는 것)
//       세번째 true,false : -p 또는 --print  다음에 프린트 할 argument 를 받는다.
//       네번째 Message : -h를 사용했을때 -p 명령어를 설명해줄 문구를 적는다.


         
         cline = clp.parse(opts, args);
         // 옵션과 main의 String[] args를 가져온다.  


        }catch (ParseException e) {
         System.out.println("error");
            usage();
            return;                                                                                    
            // 에러 발생 하였을때 usage(); 로 이동하여 help를 선언했을때와 같은 내용을 보여준다. (명령어 사용법)
        }
       

       // List와 String[] 선택가능.
        List list = cline.getArgList();
       
        for(int i=0;i<list.size();i++){
        System.out.println("list::"+list.get(i));  
        }
       
        if (cline.hasOption("p")) {   
             //-p 나  --print 옵션이 들어오면 실행, 다른 명령어를 받는 경우에 "p"를 변경하거나 추가 생성
            System.out.println(cline.getOptionValue("p"));
           
        }
  
     if (cline.hasOption("h")) {    
         // -h 나 --help 옵션이 들어오면 실행, -h나 -help를 사용했을때 에러페이지로 이동해 각 명령어들에 argument를 보여준다.        
    
         usage();
     }
}
    private static void usage() {
        HelpFormatter hf = new HelpFormatter();
        String runProgram = "java "+CliTest.class.getName() + " [options]";
        hf.printHelp(runProgram, opts);
    }
}

```


