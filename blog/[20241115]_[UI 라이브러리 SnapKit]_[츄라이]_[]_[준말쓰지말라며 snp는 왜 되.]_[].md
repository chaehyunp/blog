
코드베이스로 UI를 짜게되면 매번 뷰 사이의 관계를 정해주어야 하는데, 그것은 매우 복잡한 일이다.</br>
이를 조금 더 간결하게 작성할 수 있도록 도와주는 서드파티 라이브러리가 있다.


>**🤔 서드파티?** </br>
애플이 공식적으로 제공하는 툴인 퍼스트파티와 달리, 제 3자가 제공하는 툴을 말한다.</br>
CocoaPods, SPM(Swift Package Manager), Carthage 등을 이용해서 서드파티 라이브러리를 프로젝트에 받아올 수 있다.

</br>

츄라이해보자.

1️⃣ 'swift snapkit'을 검색해주고 깃허브에 올라온 오픈소스 링크를 감사한 마음을 담아 복사한다.

<img width="660" alt="스크린샷 2024-11-14 오후 10 57 04" src="https://github.com/user-attachments/assets/226708af-24fe-4058-8c80-16ff97b25f74">

<img width="660" alt="스크린샷 2024-11-14 오후 10 57 25" src="https://github.com/user-attachments/assets/8a431e17-c226-4968-b9e0-94ecbf9e8724">

우측에 파란색 Code 버튼 누르면 링크가 나온다. 복사해서 잠시 간직해두기.


2️⃣ 프로젝트 파일로 돌아와, Genral 탭에서 내리다보면 Frameworks, Librarie... 가 나온다 여기서 플러스를 눌러준다.

<img width="1136" alt="스크린샷 2024-11-14 오후 10 55 53" src="https://github.com/user-attachments/assets/0c3ba9c1-b030-4f08-9727-a5be5214cb0d">

<img width="455" alt="스크린샷 2024-11-14 오후 10 57 58" src="https://github.com/user-attachments/assets/783ccd94-1813-4365-bcd5-93bb6101633b">

튀어나온 모달에서 하단 `Add Other...` 클릭


<img width="455" alt="스크린샷 2024-11-14 오후 10 58 05" src="https://github.com/user-attachments/assets/7d11168d-a788-490d-9443-d6dc35cbb805">

`Add Package Dependency...` 클릭


3️⃣ 패키지를 찾아와 추가한다.

<img width="660" alt="스크린샷 2024-11-14 오후 10 58 15" src="https://github.com/user-attachments/assets/e5e70e40-97d0-49fd-aa95-d63e790a12d9">

우측 상단 서치란에 복사해두었던 링크를 붙여넣는다.


<img width="660" alt="스크린샷 2024-11-14 오후 10 58 29" src="https://github.com/user-attachments/assets/d30409db-fee5-45d8-af3b-fc0c99e36a26">

`Add Package` 클릭


<img width="242" alt="스크린샷 2024-11-14 오후 10 58 39" src="https://github.com/user-attachments/assets/149f9806-43f4-4105-95fe-1ab57a6550c1">

좌측 네비게이터에 새초롬히 자리를 튼 것을 볼 수 있다.

</br>

---

</br>

SnapKit을 사용할 본인의 스위프트 파일 최상단에서 `import SnapKit`이 될 경우 라이브러리를 잘 가져온 것이지만, 나는 `No such module 'SnapKit'`이 떴다. 🥵
</br>
바로 이 부분에서 문제였다. Xcode 프로젝트 생성시 최하단에 Include Tests를 체크하고 생성하게 되면 자동으로 기본 테스트 코드들을 만들어준다. 따라서 바로 `Add Package`할 것이 아니라 **어떤 모듈에 추가할 것인지 지정해준 후에 추가**해주어야 한다.

<img width="660" alt="스크린샷 2024-11-14 오후 11 34 13" src="https://github.com/user-attachments/assets/f8c10661-ab18-45fc-9cf7-91bc64017492">


근데 또 문제 발생 🚨

<img width="660" alt="스크린샷 2024-11-14 오후 11 48 23" src="https://github.com/user-attachments/assets/5cb76083-a8ec-48c0-85d6-ae8acff6230b">

SnapKit이 아닌 SnapKit-Dynamic로 인한 문제로 보였다.

<img width="660" alt="스크린샷 2024-11-14 오후 11 33 53" src="https://github.com/user-attachments/assets/32b025e2-da37-4109-8d4f-6fdc870c1181">

아까 처음 라이브러리를 추가했던 섹션으로 가보면 SnapKit이 아닌 다이내믹한 친구가 듀오로 따라붙어 있다.

<img width="660" alt="스크린샷 2024-11-14 오후 11 48 14" src="https://github.com/user-attachments/assets/881fc084-6449-4e45-9825-f7ce8ac4099d">

선택후, 좌측 하단 마이너스 버튼 눌러주면 예쁘게 잘 돌아간다.