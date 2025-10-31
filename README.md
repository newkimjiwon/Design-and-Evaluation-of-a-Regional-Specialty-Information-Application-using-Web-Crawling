# Design and Evaluation of a Regional Specialty Information Application using Web Crawling

● 개발 기간 : 2024.06 ~ 2024.08 <br/>
● 참여 인원 : 2 <br/>
● 사용 언어 : Kotlin <br/>
<br/> 웹 크롤링을 이용한 지역 특산품 정보 애플리케이션 개발 및 평가 (2024. 12) 한국정보기술학회논문지, 2024, vol.22, no.12, pp. 201-208 (8 pages)

<br/> ● 본 연구는 K-문화의 인기로 활성화된 한국 관광 산업에서, 관광객의 정보 접근성을 높이고 지역 경제 활성화를 도모하기 위해 지역별 특산품 정보를 통합 제공하는 애플리케이션을 개발·평가함
<br/> ● 웹 크롤링을 활용하여 분산된 지역 특산품 정보를 한 곳에 모아 제공함으로써, 관광객의 정보 접근성과 특산품 구매 용이성을 개선하는 효과를 확인함.
<div style="display: flex; align-items: center; justify-content: space-between;">
  <img src="https://github.com/user-attachments/assets/122cc4a7-f220-4691-86a8-7b53335b19da" alt="사용자(그림 1)" width="133">
  <img src="https://github.com/user-attachments/assets/13c1841b-9da0-4e73-8f4c-10c5f0af6d2e" alt="사용자(그림 2)" width="133">
  <img src="https://github.com/user-attachments/assets/7e0de084-12ca-4487-a40e-dfdb2a739e82" alt="사용자(그림 3)" width="133">
  <img src="https://github.com/user-attachments/assets/b4c64996-2234-43ac-8003-802496f7fb1e" alt="그림6 경주" width="133">
  <img src="https://github.com/user-attachments/assets/9caf196d-41ee-4808-a115-fd8fe02caeeb" alt="그림7 경주" width="133">
  <img src="https://github.com/user-attachments/assets/9819ded2-794b-4180-9b47-e4a477154b6c" alt="그림8 경주" width="133">
</div>

<br/>

## Application Architecture

<div style="display: flex; align-items: center; justify-content: space-between;">
  <img src="https://github.com/user-attachments/assets/3e3b7479-4df1-42d2-8def-cd680efea854" alt="프로그램 구조" width="800">
</div>

### 크롤링으로 수집한 데이터 및 Google OAuth를 통해 인증 및 사용자 정보를 처리
서버에서 크롤링을 통한 데이터 수집과 클라이언트와 서버 트랜잭션 처리를 보여준다. 로그인(Login component)은 Google OAuth Server과 정보를 교환하게 된다. 로그인 정보가 유효한 경우 인증코드(Auth code)를 발행하고 사용자 식별 값(UID)과 이메일(Email) 정보를 서버로 전달한다. 그리고 전달된 정보는 유저 데이터베이스에 저장한다. 특산품 정보는 웹 크롤링을 이용하여 수집되며 수집된 데이터는 MySQL connector를 이용하여 서버의 특산품 데이터베이스에 저장한다. 기념품의 개수를 표기하기 위한 아이디(Id)와 지역별로 구분하기 위해 지역(Region) 정보가 추가되어 특산품 데이터베이스에 저장된다.

<br/>

## Data

<div style="display: flex; align-items: center; justify-content: space-between;">
  <img src="https://github.com/user-attachments/assets/f7a34e53-8b49-47f7-a522-3a9eae14f384" alt="데이터 트리" width="500">
  <img src="https://github.com/user-attachments/assets/2bac10a3-dd19-4854-99b1-f07ada6d141f" alt="아이템 정보" width="500">
</div>

<br/>

### 특산품 데이터베이스 JSON 형식
특산품 데이터베이스에 저장한 특산품 데이터의 구조를 나타낸다. 지역은 여러 개의 특산품의 레코드와 연결되며 특산품은 아이디(Id), 지역(Region), 상품명(Name), 가격(Price), 대표 이미지(Url Image) 필드를 포함한다. 특산품은 판매점(Store)과 일대일(1:1) 관계를 가지며 사용자후기(User review)와 일대다(1:N) 관계를 가진다. 판매점은 이름(title), 주소(address), 위도(lat), 경도(lng) 필드를 포함한다. 사용자 후기는 주소(Url), 상품명(name), 대표 이미지(Url Image), 대표 제목(Url Title) 필드를 포함한다. 사용자에 의해 선택된 지역정보는 클라이언트에서 서버로 요청하게 되며, 서버는 특산품 데이터베이스로부터 JSON 형식으로 특산품이 포함된 지역 데이터를 반환한다.

클라이언트로 전송된 지역 데이터는 데이터의 형태에 따라 뷰(View)와 지도(Map)로 전달된다. 뷰는 가격, 이름, 판매점 주소, 특산품의 수, 대표 이미지를 리스트 형태로 보여준다. 그리고 위치정보는 지도로 전달되어 마커 형태로 위치의 정보를 제공한다.

<br/>

## Web crawling(Selenium)


<br/>

## Task Assignment
김지원: 어플리케이션 이벤트 처리 및 EC2 통신 연결, AWS EC2 인스턴스 가상머신(통신, 데이터베이스 구축)

