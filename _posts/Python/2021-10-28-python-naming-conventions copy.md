---
title: python naming conventions
date: 2021-10-28 10:57:00
categories: [Python]
tags: [python, naming]
---

## 일반적인 Naming Styles
우선 일반적으로 구별되는 [naming styles](https://www.python.org/dev/peps/pep-0008/#descriptive-naming-styles) 에 대해 알아보자.

- `b (single lowercase letter)`
- `B (single uppercase letter)`
- `lowercase`
- `lower_case_with_underscores`
- `UPPERCASE`
- `UPPER_CASE_WITH_UNDERSCORES`
- `CapitalizedWords (or CapWords, or CamelCase)`
- `mixedCase`
- `Capitalized_Words_With_Underscores (ugly!)`
- `_single_leading_underscore`
    - 약한 "내부 사용" 표시. 예를 들어 import 시 _로 시작하는 객체는 가져오지 않는다.
- `single_trailing_underscore_`
    - python 키워드와 충돌을 피하기 위해 사용된다.
    - ex) `tkinter.Toplevel(master, class_='ClassName')`
- `__double_leading_underscore`
    - Name mangling 을 수행한다. (해당 이름을 다시 정의하게 된다.)
    - 파이썬에서는 `FooBar` 클래스 안에 `__boo` 변수가 있으면 `_FooBar__boo` 로 변환해준다.
- `__double_leading_and_trailing_underscore__`
    - Magic Method 특수 메소드를 정의할 때 사용한다.

## Python Naming Conventions
[Python Naming Conventions](https://www.python.org/dev/peps/pep-0008/#prescriptive-naming-conventions) 에 대해 몇 가지만 알아보자.

- 피해야 될 네임 : `l`, `O`, `I` 싱글 문자는 숫자 `1`, `0` 하고 헷갈릴 수 있으니 사용하지 말자
- 패키지 및 모듈 네임
    - 모듈 : `lower_case_with_underscores` 사용, 짧은 단어
    - 패키지 : 동일하지만 underscores 사용은 권장되지 않음
- 클래스 네임 : `CapWords` 사용
- 타입 변수 네임 : `CapWords` 사용, 짧은 단어
    ```jsx
    from typing import TypeVar
    
    VT_co = TypeVar('VT_co', covariant=True)
    KT_contra = TypeVar('KT_contra', contravariant=True)
    ```
    
- 함수 및 변수 네임 : `lower_case_with_underscores` 사용
- 함수 및 메서드 인수
    - 인스턴스 메소드의 첫 번째 인수에는 항상 self 사용
    - 클래스 메소드의 첫 번째 인수에는 항상 cls 사용
    - 함수 인수의 이름이 키워드와 충돌하는 경우 약어나 맞춤법 손상을 하기보단 `single_trailing_underscore_` 사용하는게 좋다.
      - ex) class 키워드명을 인수로 사용하고 싶을 때 clss 보다는 class_ 가 낫다.
- 메소드 네임 및 인스턴스 변수
    - `lower_case_with_underscores` 사용
    - 비공개 메서드 및 인스턴스 변수 : `_single_leading_underscore` 사용
    - 하위 클래스와의 이름 충돌 방지 : `__double_leading_underscore` 사용
- 상수 : `UPPER_CASE_WITH_UNDERSCORES` 사용