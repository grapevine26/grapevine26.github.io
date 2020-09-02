---
layout: post
title:  "[Python] docker에서 selenium 환경구성"
subtitle:   "Running selenium in docker with python"
categories: python
tags: python selenium docker chrome webdriver scraping crawling
comments: true
---


## 개요
> 로컬에서 개발과 이것저것 하면서 여러 개의 크롬 브라우저를 띄우기엔 무리가 있어 도커에서 셀레늄을 실행시켜 로컬 컴퓨터의 과부하를 줄이기 위함

* __버전__
  - Python 3.8.3
  - selenium 3.141.0
  - docker 19.03.12
  
## docker에 selenium 설치 및 실행
---

기본적으로 python과 docker가 준비되어있다고 가정하겠습니다.

`docker pull selenium/standalone-chrome`
`docker run --rm -d -p 4444:4444 --shm-size=2g selenium/standalone-chrome`

## python에서 docker 연결
---

options는 없어도 됩니다.

~~~python
from selenium import webdriver
from selenium.webdriver import DesiredCapabilities
from selenium.webdriver.chrome.options import Options

driver = webdriver.Remote('http://localhost:4444/wd/hub', DesiredCapabilities.CHROME, options=self.options)
~~~
