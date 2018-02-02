# Stop-out homework

## 파이썬 - 네이버 웹툰 크롤러

> 전체 페이지를 가져온다면 네이버 웹툰 사이트에 큰 부하를 주어 IP가 차단될 수 있으니 만약 전체 목록을 가져오는 테스트를 위해서는 아래 웹툰(또는 페이지가 2, 3페이지 내외인 다른 웹툰)을 사용합니다.

[http://comic.naver.com/webtoon/list.nhn?titleId=703835](http://comic.naver.com/webtoon/list.nhn?titleId=703835)

### EpisodeData클래스, 크롤러 함수 구현

```python
class EpisodeData:
    """
    하나의 에피소드에 대한 정보를 갖도록 함
    """
    def __init__(self, episode_id, url_thumbnail, title, rating, created_date):
        ...
        
    
def get_episode_list(webtoon_id, page):
    """
    고유ID(URL에서 titleId값)에 해당하는 웹툰의
    특정 page에 있는 에피소드 목록을 리스트로 리턴
    """
```

`get_episode_list`함수를 실행 한 결과를 `result`변수에 받고, 해당 변수를 순회하며 각 에피소드의 정보를 출력하는 프로그램 작성

위 클래스와 함수 정의, 실행 명령들은 `crawler.py`파일 하나로 작성합니다.

## Django - 웹툰 사이트

app이름은 `webtoon`을 사용

### `webtoon/models.py` | Webtoon, Episode모델 구현

`Episode`의 `webtoon`을 제외한 모든 필드는 `CharField`를 사용합니다.

```python
class Webtoon(models.Model):
    webtoon_id
    title
    
class Episode(models.Model):
    webtoon = models.ForeignKey(Webtoon, on_delete=models.CASCADE)
    episode_id
    title
    rating
    created_date
```

### `webtoon/views.py` | Webtoon목록, 특정 Webtoon의 Episode목록 보여주기

```python
from django.shortcuts import render

from .models import Webtoon


def webtoon_list(request):
	...


def webtoon_detail(request, pk):
	...
```

### `webtoon/urls.py` | 각각 `/`, `/3/` URL을 사용

Webtoon list는 `localhost:8000`에서 출력  
pk가 3인 Webtoon detail은 `localhost:8000/3`에서 출력

Django admin에서 데이터를 넣고 잘 출력되는지 확인 할 것

## Django의 Webtoon Model에 크롤링 코드 추가

```python
class Webtoon(models.Model):
    ...
    ...
    
    def get_episode_list(self):
        """웹에서 크롤링 한 결과로 이 Webtoon에 속하는 Episode들을 생성해준다"""
```

1번 과제에서 작성한 크롤링 코드를 활용해서, Webtoon클래스의 인스턴스 메서드를 사용해 Episode를 생성해 자동으로 DB에 저장하도록 하는 로직을 구현.

```shell
from webtoon.models import Webtoon
w = Webtoon.objects.first()
w.get_episode_list()
w.episode_set.all()
# 자동으로 해당 웹툰과 연결된 Episode가 생성되었음을 확인
<QuerySet [<Episode: 1인용 기분 | 다정함>, <Episode: 1인용 기분 | 이해>, <Episode: 1인용 기분 | 신호>, <Episode: 1인용 기분 | 온도>, <Episode: 1인용 기분 | 제자리걸음>, <Episode: 1인용 기분 | 숨>, <Episode: 1인용 기분 | 묘연>, <Episode: 1인용 기분 | 속울음>, <Episode: 1인용 기분 | 가치와 가격>, <Episode: 1인용 기분 | 하루>, <Episode: 1인용 기분 | 프롤로그>]>
```


## 제출

1번 과제인 `crawler.py`가 루트 폴더에 포함된 Django프로젝트 하나를 구성해서 새로운 GitHub저장소를 생성 후 해당 저장소 주소를 제출하세요.

`requirements.txt`작성 정확히 해주셔야 합니다!