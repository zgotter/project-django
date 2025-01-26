# Project - Django

```
project_root/
├── src/  # 또는 프로젝트명/
│   ├── boards/
│   │   ├── __init__.py
│   │   ├── models.py      # MongoDB 모델
│   │   ├── services.py    # 비즈니스 로직
│   │   ├── views.py       # 뷰 로직
│   │   ├── urls.py
│   │   └── schemas.py     # Pydantic 스키마 (선택적)
│   ├── core/
│   │   ├── __init__.py
│   │   ├── config.py      # 설정
│   │   └── exceptions.py  # 커스텀 예외
│   └── utils/
│       ├── __init__.py
│       └── decorators.py
├── templates/
│   └── boards/
│       └── list.html
└── tests/
    └── boards/
        ├── __init__.py
        ├── test_models.py
        └── test_services.py
```