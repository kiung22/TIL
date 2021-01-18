# Web crawlling

> 웹 크롤링 기초



## 라이브러리

### requests

```python
import requests 

kospi_url = 'https://finance.naver.com/sise/'
res = requests.get(kospi_url).text

```





### BeautifulSoup

```python
from bs4 import BeautifulSoup

soup = BeautifulSoup(res, 'html.parser')
text = soup.select_one('#KOSPI_now').text
```

