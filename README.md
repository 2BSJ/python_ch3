# Pycharm 에서 Django 프로젝트 시작하기

1. pycharm 프로젝트 생성(python 프로젝트)

2. Django 설치
[터미널]
pip install django

3. 장고 프로젝트 생성
[터미널]
django-admin startproject python_ch3  
문제점 - python_ch3 하위에 python_ch3 쟝고 프로젝트가 만들어짐

4. 디렉토리 정리  
   ->pycharm 프로젝트와 django 프로젝트의 디렉토리를 일치시키느은 작어업
    
5. psycopg2(postgres db lib) 설치
[터미널] pip install psycopg2

6. postgresql 에 db 생성 및 계정생성 접근 권한 부여
    -create database djdb
    -create user djdb with password 'djdb';
    -grant all privileges on all tables in schema public to djdb;
    -data/pg_hba.conf 접근 설정
    
7. settins.py 설정
    1) TIME_ZONE = 'Asia/Seuoul'
    2) DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'djdb',
        'USER': 'djdb',
        'PASSWORD' : 'djdb',
        'HOST' : '192.168.1.92',
        'PORT' : 5432
    }
}
    3) Template 디렉토리 설정
    TEMPLATE=[
        ...
        'DIRS': [os.path.join(BASE_DIR,'template')],
        ...
    ]
    
    python_ch3
        |
        |-------- templates(생성)

8. 장고 프로젝트의 기본 관리 어플리케이션이 사용하는 테이블
[터미널] python manage.py migrate

9. 장고 프로젝트의 기본 관리 어플리케이션 로그인 계정 생성하기(관리계정 생성)
[터미널] python manage.py createsuperuser 

10. 지금까지 작업 내용 확인하기
[터미널] python manage.py runserver 0.0.0.0:8888

11. 관리페이지 들어가기
localhost:8888/admin

-------------------------

# Application 작업
1. 어플레키에션 추가
[터미널] python manage.py startapp helloworld
2. 어플리케이션 등록(settings.py)
   INSTALLED_APPS =[
      'python_ch3',
       ....
       ....
   ]