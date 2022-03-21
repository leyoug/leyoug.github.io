---
title: 장고 테스트 시 모든 쿼리 찍어보기
date: 2021-09-01 09:43:00
categories: [Python, Django]
tags: [python, django]
---

## settings.py 에 LOGGING 설정
settings/local_test.py
세팅 파일에 아래 LOGGING 설정을 추가한다
- 콘솔에 쿼리 로그를 남긴다

```bash
LOGGING = {
    'version': 1,
    'filters': {
        'require_debug_true': {
            '()': 'django.utils.log.RequireDebugTrue',
        }
    },
    'handlers': {
        'console': {
            'level': 'DEBUG',
            'filters': ['require_debug_true'],
            'class': 'logging.StreamHandler',
        }
    },
    'loggers': {
        'django.db.backends': {
            'level': 'DEBUG',
            'handlers': ['console'],
        }
    }
}
```

## 테스트 코드에서 디버그 허용
test_views.py
- 테스트 클래스에 `override_settings` 를 추가하여 `DEBUG=True` 로 설정해준다


```python
from django.test.utils import override_settings

@override_settings(DEBUG=True)
class LoginTestCase(TestCase):
	...
```

테스트 코드 실행 시 발생하는 쿼리를 콘솔에서 확인할 수 있다