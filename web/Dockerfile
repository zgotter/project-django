# Python 3.11 버전의 slim 이미지를 기본 이미지로 사용
# slim 버전은 필수적인 패키지만 포함된 경량화된 이미지
FROM python:3.11-slim

# 컨테이너 내부의 작업 디렉토리를 /app으로 설정
# 이후의 모든 명령어는 이 디렉토리를 기준으로 실행됨
WORKDIR /app

# 패키지 관리자 업데이트 및 필요한 패키지 설치
RUN apt-get update && apt-get install -y \
    # 컴파일에 필요한 기본 도구
    build-essential \ 
    # curl 명령어를 사용하기 위해 설치
    curl \
    # 설치 후 사용하지 않는 패키지 목록 삭제
    && rm -rf /var/lib/apt/lists/*

# Poetry 버전을 1.7.1로 지정하는 환경 변수 설정
ENV POETRY_VERSION=1.7.1

# Poetry 패키지 관리자 설치
RUN curl -sSL https://install.python-poetry.org | python3 -

# Poetry 실행 파일의 경로를 시스템 PATH에 추가
ENV PATH="/root/.local/bin:$PATH"

# Poetry가 가상환경을 생성하지 않도록 설정
# Docker 컨테이너 내부에서는 별도의 가상환경이 불필요
RUN poetry config virtualenvs.create false

# Poetry 의존성 파일들을 컨테이너로 복사
COPY pyproject.toml poetry.lock ./

# Poetry 프로젝트 의존성 패키지들을 설치
# 대화형 프롬프트 없이 자동으로 설치
RUN poetry install --no-interaction --no-ansi

# 현재 디렉토리의 모든 파일을 컨테이너의 /app 디렉토리로 복사
COPY . .

# 컨테이너가 시작될 때 실행할 기본 명령어
# Django 개발 서버를 0.0.0.0:8000 포트로 실행
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
