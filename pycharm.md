# Pycharm 관련 설정

## 사용할 Python Interpreter 세팅

1. `cmd + ,` 또는 `ctrl + ,`로 설정 진입
2. `Project: <프로젝트명>`섹션을 클릭, `Project Interpreter`선택
3. `Project Interpreter`를 클릭, 최하단의 `Show All`클릭
4. `+`버튼을 클릭하고 `Add Local`선택
5. 인터프리터 경로를 선택하고 `OK`클릭
	- **macOS** : `/usr/local/var/pyenv/versions/<환경명>/bin/python`
	- **Ubuntu** : `/home/<유저명>/.pyenv/versions/<환경명>/bin/python`

## 단축키

터미널 열기 : `alt + f12`

### Multi Selection 단축키 설정

`Preferences` -> `Keymap` -> 검색창에 `add selection` 입력 -> `Add Selection for Next Occurrence`의 단축키 할당 (`cmd + d`를 추천)


## Pro버전에서 Django Support 켜기

1. `Preferences` -> `Language & Frameworks` -> `Django`로 이동
2. Django project root에 프로젝트의 장고 코드(소스 루트)폴더 지정
3. Settings에 config/settings.py모듈 선택
4. Manage script에 장고 코드 폴더의 manage.py모듈 선택