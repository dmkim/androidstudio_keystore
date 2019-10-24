## Android Studio 에서 빌드시 sun.security.validator.ValidatorException 해결 하기

1. Portecle GUI 다운로드 한 후 압축을 해제 하고 실행 한다.  
  https://sourceforge.net/projects/portecle/files/latest/download 에서 다운로드 한 후 압축 해제  
  압축 해제한 풀더에서 protecle.jar 을 더블 클릭 하거나 커멘트창에서 java -jar portecle.jar 입력
  
    ![Alt text](/image/Screenshot_24.png)

2. Portecle GUI 실행후 Examine -> Examine SSL/TLS Connection 선택
    
    ![Alt text](/image/Screenshot_25.png)   
  
3. dl.google.com 입력  

    ![Alt text](/image/Screenshot_26.png)   
  
4. Certificate 전부 하나씩 PEM Encoding 버튼을 눌러 Save 하여 pem 파일 저장  

    ![Alt text](/image/Screenshot_27.png)   
  
5. Open Keystore File 버튼을 눌러 설치된 Android Studio 폴더에서 다음 경로에 있는 cacerts 파일 로드  
  D:\Program Files\Android\Android Studio\jre\jre\lib\security  
  비밀번호는 changeit  
  
     ![Alt text](/image/Screenshot_28.png)   
     
     ![Alt text](/image/Screenshot_29.png)   
   
6. Import Trusted Certificate 버튼을 눌러 방금 만들어 놓은 pem 파일을 선택하여 cacerts 에 집어 넣고 저장   

    ![Alt text](/image/Screenshot_30.png)   
  
7. Android Studio 에 열려 있는 프로젝트에서 android\gradle.properties 에 cacerts 경로 추가  

```
    systemProp.javax.net.ssl.trustStore=D\:\\Program Files\\Android\\Android Studio\\jre\\jre\\lib\\security\\cacerts  
    systemProp.javax.net.ssl.trustStorePassword=changeit 
```  
8. android\gradle.properties 화면  

    ![Alt text](/image/Screenshot_32.png)   
