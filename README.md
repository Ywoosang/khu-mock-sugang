# 경희대학교 모의 수강신청 시스템 (KHU-sugang)  


![image](https://user-images.githubusercontent.com/68385605/108505223-6792da80-72fa-11eb-9eda-4a91ae408f59.png)


경희대학교 학생들의 수강신청을 돕기 위해 자체제작한 모의수강신청 프로그램입니다   
실제 수강신청과 비슷한 환경을 조성하기 위해 여러 기능을 추가했습니다 

## 배포 URL 
https://khu-sugang.herokuapp.com


## 목차

- [접속시간 테스트](#실제-수강시청과-마찬가지로-네이비즘을-이용해-접속시간을-테스트할-수-있습니다)
- [과목검색](#학수번호로-과목-검색시-로딩이-완료되면-과목이-나타납니다)
- [수강신청](#수강희망과목-또는-개설강좌검색탭에서-수강신청이-가능합니다)
- [신청완료](#수강신청버튼을-클릭하면-시간지연-후-신청이-완료됩니다)
- [과목삭제](#삭제버튼-클릭-후-완료를-클릭하면-시간지연-후-과목이-삭제됩니다)
- [신청내역확인](#수강신청내역을-신청내역-메뉴에서-별도로-확인하실-수-있습니다)
- [인원초과연습](#수강인원-초과연습이-가능합니다)
- [이수가능학점초과](#이수가능학점을-초과하면-과목이-신청되지-않습니다)
- [자동로그아웃](#시간-연장-없이-10분이상-머무를-경우-자동-로그아웃-됩니다)
- [개발환경구축](#개발-환경-구축)

## 오류 관련

오류 발견 시 isssue 로 등록해주세요  
이슈 기반 commit 으로 수정내용을  확인하실 수 있습니다  

## 기능

### 실제 수강시청과 마찬가지로 네이비즘을 이용해 접속시간을 테스트할 수 있습니다

![image](https://user-images.githubusercontent.com/68385605/108506132-ae350480-72fb-11eb-966f-d0db707a3ba1.png)
 
### 학수번호로 과목 검색시 로딩이 완료되면 과목이 나타납니다  

![image](https://user-images.githubusercontent.com/68385605/108507330-7fb82900-72fd-11eb-8e47-300b9a476ffc.png)

![image](https://user-images.githubusercontent.com/68385605/108507519-cdcd2c80-72fd-11eb-86d0-159631305a5c.png)

### 수강희망과목 또는 개설강좌검색탭에서 수강신청이 가능합니다
 
![image](https://user-images.githubusercontent.com/68385605/108511062-b2b0eb80-7302-11eb-8df8-44051a1add14.png)

![image](https://user-images.githubusercontent.com/68385605/108511062-b2b0eb80-7302-11eb-8df8-44051a1add14.png)

### 수강신청버튼을 클릭하면-시간지연 후 신청이 완료됩니다

![image](https://user-images.githubusercontent.com/68385605/108506440-200d4e00-72fc-11eb-922d-9d31e55a3133.png)

### 삭제버튼 클릭 후 완료를 클릭하면 시간지연 후 과목이 삭제됩니다

![image](https://user-images.githubusercontent.com/68385605/108509988-4d102f80-7301-11eb-8181-b8712c689533.png)

![image](https://user-images.githubusercontent.com/68385605/108511484-53071000-7303-11eb-9436-259367939aad.png)

### 수강신청내역을 신청내역 메뉴에서 별도로 확인하실 수 있습니다

![image](https://user-images.githubusercontent.com/68385605/108506854-cce7cb00-72fc-11eb-9c1e-a375c6513c91.png)

### 수강인원 초과연습이 가능합니다 
 
![image](https://user-images.githubusercontent.com/68385605/108506690-8e521080-72fc-11eb-9496-8eb74a9d8724.png)

### 이수가능학점을 초과하면 과목이 신청되지 않습니다

![image](https://user-images.githubusercontent.com/68385605/108511684-96617e80-7303-11eb-8fbc-2be1795ff819.png)

### 시간 연장 없이 10분이상 머무를 경우 자동 로그아웃 됩니다

![image](https://user-images.githubusercontent.com/68385605/108507027-1506ed80-72fd-11eb-8287-44f8a7fa2ca4.png)


## 개발 환경 구축 

node.js 와 vue 가 설치되어 있어야 합니다

### node.js install 

ubuntu 기준 nvm 이용을 추천합니다 
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash 
source ~/.bashrc 
nvm install v14.15.4 
``` 

### vue cli install 
```
npm install -g @vue/cli 
``` 

### Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```
