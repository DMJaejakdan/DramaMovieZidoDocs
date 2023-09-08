# 하둡 실습을 위한 EC2 발급

마지막 작성 날짜: 2023-09-08 <br>
작성자: 김예진

# 1. 구글 계정 및 AWS 계정 생성

프리티어 EC2 발급을 위해 구글 계정과 AWS 계정을 생성합니다. 이하 과정은 생략합니다. 

# 2. Add MFA for root user

MFA(Multi-Factor Authentication)는 사용자 이름 및 암호 로그인 보안 정보 외에 두 번째 인증 요소가 필요하게 설정하는 인증 방식입니다. AWS 계정에 생성한 루트 및 IAM 사용자에 대해 MFA를 활성시킬 수 있습니다(출처: [aws](https://aws.amazon.com/ko/iam/features/mfa/#:~:text=AWS%20multi%2Dfactor%20authentication%20(MFA,have%20created%20in%20your%20account.))). 

1. IAM service 페이지 접속
2. Security recommendations에서 Add MFA for root user 클릭

