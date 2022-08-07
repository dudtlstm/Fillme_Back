## 프로젝트 실행 방법(순서대로 진행하기)

### 1. 레퍼지토리 클론
    git clone https://github.com/LikeLion-at-DGU/Fillme_Back.git

### 2. 가상환경 실행
    source myvenv/Scripts/activate

### 3-a. 라이브러리 설치
    pip install -r requirements.txt

### 3-b. reqirements.txt로 필요한 라이브러리 설치가 안된다면
    pip install django
    pip install djangorestframework
    pip install django-cors-headers
    pip install djangorestframework-simplejwt
    pip install dj-rest-auth
    pip install django-allauth
    pip install pillow

### 4. 프로젝트 폴더 위치로 이동 (manage.py 파일이 있는 위치)
    cd cloud

### 5. DB 마이그레이션
    python manage.py makemigrations
    python manage.py migrate

### 6. 서버 실행
    python manage.py runserver

## API

### 유저 회원가입 및 로그인/로그아웃

### 127.0.0.1:8000/accounts - POST 메소드 사용
    username, email, password1(비밀번호), password2(비밀번호 확인) 입력
    ex)
    {
        "username" : "유저네임 입력",
        "email" : "이메일형식 입력",
        "password1" : "비밀번호",
        "password2" : "비밀번호 확인"
    }

### 로그인
### 127.0.0.1:8000/accounts/login - POST 메소드 사용
    username, password 입력
    ex)
    {
        "username" : "유저네임",
        "password" : "비밀번호"
    }

### 로그아웃
### 127.0.0.1:8000/accounts/logout - POST 메소드 사용
    입력값 없이 POST방식으로 보내기


### 유저 메인 프로필 조회 및 수정(회원가입시 자동으로 생성되기 때문에 빈값의 프로필을 수정한다는 개념)
### 내 프로필
### 127.0.0.1:8000/mypage - GET 메소드 사용
#### 결과
    {
        "user" : "유저의 id 값(정수)",
        "fullname" : "성명",
        "memo" : "한줄소개",
        "color" : "색상",
        "image" : "프로필 사진"
    }

#### 프로필 사진은 파일 형식
#### color는 선택지가 있음
#### 프론트에서 가져올때 : profile.category 는 키값(ex. 'pink'), profile.get_category_display 는 내용(ex. '#FEBCC0')

    COLOR_LIST = (
            ('pink', '#FEBCC0'),
            ('red', '#83333E'),
            ('lorange', '#FFB37C'),
            ('orrange', '#FF9A50'),
            ('yellow', '#FFE886'),
            ('green', '#153D2E'),
            ('lblue', '#8692CC'),
            ('blue', '#486FBB'),
            ('navy', '#1C0F67'),
            ('lpurple', '#8878E1'),
            ('purple', '#4D2E66'),
            ('etoffe', '#827165'),
            ('brown', '#231819'),
            ('gray', '#464648'),
            ('black', '#010101'),
        )

### 내 프로필 수정
### 128.0.0.1:8000/mypage/profile_update - PATCH 메소드 사용
    {
        "fullname" : "성명",
        "memo" : "한줄소개",
        "color" : "색상",
        "image" : "프로필 사진"
    }

### 다른 유저 프로필 조회
### 128.0.0.1:8000/mypage/<int:id> - PATCH 메소드 사용
#### 결과
    {
        "user" : "유저의 id 값(정수)",
        "fullname" : "성명",
        "memo" : "한줄소개",
        "color" : "색상",
        "image" : "프로필 사진"
    }