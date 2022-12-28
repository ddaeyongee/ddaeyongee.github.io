---


title:  "[ios] 어플리케이션 발행하기"
date: 2022-12-28 15:33:00 +0900
last_modified_at: 2022-12-28 15:33:00 +0900
header:
  teaser: /assets/images/unsplash/github-842ofHC6MaI.jpg
  overlay_image: /assets/images/unsplash/github-842ofHC6MaI.jpg
  overlay_filter: 0.5
  caption: "Photo credit: [**Unsplash**](https://unsplash.com/photos/842ofHC6MaI)"

toc: true
toc_sticky: true

tags:
  - ios
  - appclication
  - appstore
  - apple
---

## 사전준비 

- iOS 발행은 맥북 필요.  
- Xcode도 앱스토어에서 찾아서 설치.  
- Apple Developer Program에 개발자로 가입해야 합니다. (참고 가입시 비용 발생. 1년에 13만원 정도)

## 버전체크

  앱을 빌드하기 전  
  지금 발행하는 앱의 버전을 수정하고 싶으면 pubspec.yaml 파일에서 기록하고 pub get 누르면 됩니다.  
  version: 1.0.0+1  
  이런 부분이 있을텐데 맘대로 바꾸면 됩니다.  
  1.0.0은 버전넘버, +1은 버전코드입니다.  
  대격변 업데이트를 하면 2.0.0 이렇게 첫째 숫자를 +1 하는게 일반적이고  
  마이너한 기능추가는 1.1.0 이렇게 둘째 숫자를 +1 하는게 일반적이고  
  자잘한 수정사항 패치는 1.0.1 이렇게 셋째 숫자를 +1 하는게 일반적입니다.  


## 애플 개발자 등록

https://developer.apple.com/programs/  
들어가서 애플아이디로 로그인하고 apple developer program 에 enroll 해봅시다.  
첫 결제시 하루 이틀 정도 기다려야합니다.

## Xcode에서 설정확인하기

ios폴더를 우클릭해서 Xcode에서 오픈하기 누르고 시작하면 됩니다.  
Xcode 왼쪽 파일트리에서 젤 위의 Runner 눌러보시면 뭐가 뜹니다.  

![ios-app-store-connect-1](/assets/images/ios-app-store-connect-1.png)

1. Bundle Identifier를 확인합니다.  
   이게 앱스토어에서 앱들을 구분짓는 유니크한 아이디입니다.  
   com.회사명.프로젝트명으로 알아서 채워주는게 맘에 안들면 바꾸면 됩니다.  

   바꾸려면 안드로이드 스튜디오 상단 View - Tool Windows - Terminal 누르고  
   dart pub global activate rename 입력하고  
   dart pub global run rename --bundleId com.회사명작명.앱이름작명  
   입력하면 됩니다.  
   회사명 없으면 맘대로 가상의 회사를 만들어요.  
   (주의) 앱이름, 회사이름에 _ 언더바 있으면 안 됩니다.  

2. 버전이 pubspec.yaml이랑 다르면 그냥 맞추세요.  
3. 중간 Deployment info 란에서 iOS 버전은 기본 셋팅되어있는거 그대로 쓰면 됩니다. 특정 iOS버전에만 배포하려고 할 때 수정하면 됩니다.  
4. 하단 App Icons and Launch Images 메뉴에서 앱 아이콘 이미지 확인도 가능합니다.  

   android/ios용 앱 아이콘 변경은 flutter_launcher_icons 이런 패키지 찾아서 설치해서 쓰는게 간단하고 좋습니다.  

## developer.apple.com/ 접속

![ios-app-store-connect-2](/assets/images/ios-app-store-connect-2.png)

https://developer.apple.com/account/  
Account 페이지에서 certificates, identifiers & profiles 메뉴를 눌러봅니다.  
거기서 Identifiers 메뉴에서 App ID 새로만들기 이런거 누르시면 됩니다.  

![ios-app-store-connect-3](/assets/images/ios-app-store-connect-3.png)

▲ App ID 만든다고 하면 됩니다.  
타입정하라고 나오면 App Clip 말고 App 으로.

![ios-app-store-connect-4](/assets/images/ios-app-store-connect-4.png)

▲ 앱 설명을 영어로 잘 적고 Bundle ID를 여기에 잘 기록하면 되는데  
Bundle ID는 아까처럼 Xcode에서 확인할 수 있습니다.  
하단에 Capabilities에 내 앱이 사용중인 항목이 있다면 체크합시다. 아마 없을듯  

![ios-app-store-connect-5](/assets/images/ios-app-store-connect-5.png)

▲ https://appstoreconnect.apple.com/  
여기로 들어가서 앱을 눌러봅니다. 그리고 새 앱을 만들어 봅시다.  

![ios-app-store-connect-6](/assets/images/ios-app-store-connect-6.png)

▲ 그리고 여러가지 정보를 기입하면 됩니다.  
SKU는 여러분만 볼 수 있는 앱 이름입니다.  
그리고 이제 Xcode 가서 archive 빌드하면 끝  

## Xcode로 돌아와서 마지막 확인

![ios-app-store-connect-7](/assets/images/ios-app-store-connect-7.png)

▲ Xcode를 다시 켜봅니다.  
앱에 서명해야 앱스토어에 올릴 수 있습니다.  
1. 자동 서명하기 버튼이 체크되어있는지 확인합시다.  
   체크안하면 수동으로 서명해야 한다.  
2. Team 항목에서 개발자 등록된 계정도 선택해야 함  

![ios-app-store-connect-8](/assets/images/ios-app-store-connect-8.png)

▲ Failed to create provisioning profile 에러가 나는 경우  
상단메뉴 Product - Destination - My Mac 을 선택하고 하단에 Try again 버튼을 누르면 해결됩니다.  
그래도 안되면 상단 Xcode - Preferences - Account 메뉴에서 개발자계정으로 로그인했는지 확인.  

![ios-app-store-connect-9](/assets/images/ios-app-store-connect-9.png)

▲ 이제 Xcode 상단메뉴에서  
Product - Destination - Any iOS device 누르시고  
Product - Archive 누르면 됩니다.  
- 중간에 뭐 선택하라고하면 App Store Connect로 발행하기 누르면 됩니다.  

  혹시 플러터 프로젝트에 문법에러같은게 있으면 실패할텐데  
  정확한 에러메세지는 Xcode 좌상단 세모 아이콘 눌러보면 됩니다.  
  
  애플이 1~3일 심사해주고 심사결과를 알려 줍니다.  
  앱 관리는 App Store Connect에서 해주면 됩니다.  