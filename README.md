# 🏪 BackEnd 프로젝트

## 👀 서비스 소개
- 서비스명 : Trip Serivice
- 서비스설명 : 지역별로 여행에 관한 정보를 제공한다.

## 📅 프로젝트 기간
- 2023.09.24 ~ 2023.09.24 

## ⭐ 주요 기능
지역별 관광지 정보 수집
관광지, 문화시설, 축제공연행사,여행,레포츠,숙박,쇼핑,음식점 등으로 조회
회원 관리 기능
로그인 관리
게시판 기능

## 기본기능

### 1.사용자 비밀번호 암호화 
1. 해시 함수와 salt 및 key 이용 사용자 비빌번호 암호화

2. 적용 알고리즘 : SHA-256

3. 알고리즘 개요
   SHA-256은 "안전한 해시 알고리즘 256비트"라는 의미로, 암호학적으로 안전한 해시 함수 중 하나입니다. 해시 함수는 임의의 길이의 데이터를 고정된 길이의 해시 값으로 변환하는 수학적 함수입니다. 이러한 해시 함수는 데이터 무결성을 검증하거나 데이터를 식별하기 위해 사용됩니다. SHA-256은 SHA-2 (Secure Hash Algorithm 2) 패밀리의 일부로, 다양한 애플리케이션에서 데이터 무결성을 검증하거나 디지털 서명을 생성하는 데 사용됩니다.

SHA-256은 다음과 같은 특징을 가집니다:

고정된 길이: SHA-256 해시 값은 항상 256비트(32바이트)로 고정되어 있습니다.

단방향: 해시 함수는 입력 데이터를 해시 값으로 변환할 때, 반대 방향으로 돌아갈 수 없도록 설계되어 있습니다. 즉, 해시 값으로부터 원래 데이터를 복원할 수 없습니다.

충돌 저항성: SHA-256은 두 개의 서로 다른 입력 데이터에 대해서도 같은 해시 값을 생성할 확률을 매우 낮게 만드는 충돌 저항성을 가지고 있습니다. 이는 데이터 무결성을 보장하기 위해 중요합니다.

무작위성: 작은 입력 변경이 해시 값에 큰 변화를 일으키므로, 무작위성과 비슷한 특성을 가집니다.

암호학적으로 안전: SHA-256은 암호학적으로 안전한 해시 함수로 간주됩니다. 이는 해시 값을 생성하기 위해 충분히 복잡한 알고리즘을 사용하여, 무작위성과 예측 불가능성을 확보하기 위한 것입니다.

SHA-256은 비트코인과 같은 암호화폐 기술에서 블록 체인의 무결성을 검증하거나, 데이터베이스에서 비밀번호를 안전하게 저장하는 데 사용되며, 다양한 보안 및 암호학 애플리케이션에서 널리 사용됩니다.

키 스트레칭 
반복된 해시 함수 적용: 사용자의 비밀번호나 다른 암호화 키를 입력으로 받고, 여러 번의 반복을 통해 해시 함수(예: PBKDF2, bcrypt, scrypt)를 적용합니다. 이렇게 하면 암호화 키 생성에 시간이 더 오래 걸리게 됩니다.

솔트(salt) 사용: 암호화 키를 생성할 때 솔트라고 불리는 무작위 값이 추가됩니다. 이 솔트는 같은 비밀번호를 가진 여러 사용자에 대해 다른 암호화 키를 생성하도록 도와줍니다. 공격자는 여러 사용자에 대한 키를 하나씩 공격해야 하므로 공격을 어렵게 만듭니다.

많은 반복 횟수: 암호화 키를 생성할 때 반복 횟수를 늘리면, 암호화 키를 생성하는 데 더 많은 시간이 걸립니다. 이는 공격자가 대규모 연산을 수행해야 하므로 공격을 어렵게 만듭니다.

적용 서비스 : 회원가입, 로그인  (MemberServiceImpl의  registerMember, login) 
![image](https://github.com/dev1week/with-dog/assets/119592507/744ea3f7-bfb9-43a3-8667-9b94147c8e46)


5. 적용 서비스 개발 개요
![image](https://github.com/dev1week/with-dog/assets/119592507/946dbce2-12df-4d39-a3b4-2af70875398c)
![image](https://github.com/dev1week/with-dog/assets/119592507/495238b9-3a6b-4827-9295-8076df5767de)



### 2. KMP 활용 관광지 검색어 활용 검색 
1. KMP 이용 관광지 검색 기능 

2. 적용 알고리즘 : KMP

3. 알고리즘 개요
  접두사-접미사 테이블 생성: 검색하려는 문자열(패턴 문자열)에서 접두사와 접미사가 일치하는 최대 길이를 저장하는 접두사-접미사 테이블을 생성합니다.

문자열 검색: 텍스트 문자열을 한 문자씩 왼쪽에서 오른쪽으로 검색하면서 패턴 문자열과 일치하는 부분 문자열을 찾습니다.

일치하지 않는 경우 이동: 일치하지 않는 문자가 발견되면, 패턴 문자열을 이동할 때 몇 개의 문자를 건너뛰어야 하는지 결정하는데, 이때 접두사-접미사 테이블을 활용합니다. 이동 거리를 미리 계산하여 불필요한 문자 비교를 줄입니다.

KMP 알고리즘은 최악의 경우에도 선형 시간(O(N+M))에 패턴 문자열을 검색할 수 있으며, 특히 텍스트와 패턴이 긴 경우에 빠르게 동작합니다. 이 알고리즘은 문자열 검색에서 문자 비교 횟수를 최소화하여 효율성을 높이는 데 중점을 두고 있습니다.

4. 적용 서비스 : 관광지 검색  
![image](https://github.com/dev1week/with-dog/assets/119592507/1f3712d9-2502-4644-8bf3-956dcf1d93c1)
![image](https://github.com/dev1week/with-dog/assets/119592507/aeb7c626-954c-44a3-bc70-e2cb7f6a8393)


5. 적용 서비스 개발 개요
![image](https://github.com/dev1week/with-dog/assets/119592507/34cc616c-287e-4e12-a637-a673f1d7d4f2)
![image](https://github.com/dev1week/with-dog/assets/119592507/e0ec2e8b-2794-426f-978c-0f02369b4810)





### 3. 회원 정보 페이지

#### 1) 회원 가입
![image](https://github.com/dev1week/enjoyTrip/assets/119592507/e44aff8b-ec50-4e56-ae04-39ab6f0fee3b)
![image](https://github.com/dev1week/enjoyTrip/assets/119592507/f08716ea-08c7-4fb6-80bf-d9372bc26759)


- 메인페이지에서 회원가입 클릭 시 이동
- 회원가입 기능 구현 

#### 2) 회원 정보 조회
![image](https://github.com/dev1week/enjoyTrip/assets/119592507/9746309e-f6fa-4fb5-a7d6-287b5df040b8)


- 로그인 시 navbar에서 이동 가능
- 마이페이지 이동 시 회원 정보 조회
- 비밀번호는 뜨지 않게 처리.

#### 3) 회원 정보 수정
![image](https://github.com/dev1week/enjoyTrip/assets/119592507/7ddeb701-66b1-4115-b966-12d7ecef60f8)


- 마이페이지에서 수정 버튼을 클릭시 회원 정보 수정 가능
- 아이디를 제외한 비밀번호, 이름, 이메일 수정 가능 
- 수정 버튼을 누르면 비밀번호를 뜨게 처리.

#### 4) 회원 정보 삭제(탈퇴)
![image](https://github.com/dev1week/enjoyTrip/assets/119592507/dbda3850-4b91-45fe-b2f4-c1b62871c9d7)


- 마이페이지에서 탈퇴 버튼을 누르면 회원 정보 탈퇴 가능
- 탈퇴 시 메인 화면으로 돌아감.

#### 5) 로그인 / 로그아웃
![image](https://github.com/dev1week/enjoyTrip/assets/119592507/f08716ea-08c7-4fb6-80bf-d9372bc26759)

- 메인 화면에서 아이디, 비밀번호 입력 후 로그인 버튼 클릭 
- 로그인되었을 경우 navbar 변경
- 로그인이 된 상태에서 navbar에 있는 로그아웃 버튼 클릭 시 로그아웃 기능.


- 검색 후 결과 지도 마킹 기능

### 6. 검색결과 표시 후 드래그 하여 계획에 포함
![Screen Recording - Sep 8, 2023](https://github.com/dev1week/with-dog/assets/119592507/a4c019a7-1ff4-4c67-999a-ba561d25e91e)
![image](https://github.com/dev1week/with-dog/assets/119592507/bb6f1346-74e7-4712-8e77-80c1a800fa32)
![image](https://github.com/dev1week/with-dog/assets/119592507/582a7764-ee92-4e73-9e70-fef5d4e6bb95)




- 검색 후 좌측 화면에 검색 결과 표현
- 마음에 드는 지역을 드래그하여 계획에 추가가능

### 7. 여행 계획 경로 설정 (계획은 로컬스토리지 저장)
![image](https://github.com/dev1week/with-dog/assets/119592507/849bcf7e-9e73-4054-9f2b-7aca2070f23a)



- 오른쪽 상단에 계획으로 넣어놓은 장소는 이름과 주소를 배열로 저장하여 **local storage에 저장**

### 8. 최종 여행 계획 표시
![image](https://github.com/dhflxhdxhd/with-dog/assets/52151533/44f08d1e-daa2-4c36-aeb8-e832fe2b9c91)



## 👨‍💻팀원 소개

- 김아현
- 김한주
