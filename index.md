---
title       : My Lectures
author      : Issac Lee
framework   : minimal
hitheme     : solarized_light
mode        : selfcontained
github      : {user: issactoast,
               repo: SlidifyLectureTest,
               branch: gh-pages}
---

# Slidify를 이용한 렉쳐노트 페이지 만들기(실험)

<a href="http://prose.io/#issactoast/SlidifyLectureTest/edit/gh-pages/index.Rmd" class="button icon edit">Edit Page</a> 







이것은 Slidify를 사용하는 과정을위한 빠른 웹 사이트를 만들기위한 템플릿입니다. 소스 파일 을 구성 `site.yml`하고 편집 한 후에 는 루트에서 `Rmd`실행 `blogify(".")`하면됩니다. Slidify는 자동으로 모든`Rmd`파일을 감지하고 슬라이드 한 다음 색인 페이지와 함께 모든 강의 슬라이드를 만듭니다.

`blogify(".")` 함수를 실행하기 위해서는 반드시 다음의 세개의 팩키지 설치에 성공해야하며, `blogify(".")` 함수 실행시 `R`에 아래의 세개 팩키지를 로드하고 있어야한다.

 - library(slidify)
 - library(slidifyLibraries)
 - library(poirot)


이 샘플 과정 웹 사이트는 실제로 정확히 같은 방식으로 생성되었습니다.

## 구조

가장 먼저 이해해야 할 것은 폴더 구조입니다. `lectures` 폴더에는 강의 슬라이드, 강의 당 하나 의 하위 폴더가 있습니다.

```
assets      -> put custom img/js/css/layout assets
lectures    -> folder containing lectures
  01
  02
  03
libraries   -> frameworks, highlighters and widgets
index.Rmd   -> Rmd source for home page
site.yml    -> Site related configuration
```

##구성

이 파일 `site.yml`에는 사용자 정의해야 할 특성이 들어 있습니다. `site.yml` 파일에 자신의 github ID와 repo를 업데이트 해줘야함.


## 강의 리스트 자동 업데이트

다음 코드 덩어리를 추가하여 강의 목록을 자동으로 `index.Rmd`에 쉽게 추가 할 수 있습니다. 동일한 폴더 구조 및 명명 체계를 사용하고 있다고 가정합니다. 다른 스키마를 사용하는 경우이 코드 조각에서 코드를 조정해야합니다.

```
{r echo = F, results = 'asis'}
lectures = dir('lectures', full = TRUE)
links = paste0(seq_along(lectures), ". ",
               "[Lecture ", basename(lectures), "]",
               "(", lectures, "/index.html)")
writeLines(links)
```

위 코드 덩어리를 실행 한 결과입니다.

1. [Lecture 01](lectures/01/index.html)
2. [Lecture 02](lectures/02/index.html)
3. [Lecture 03](lectures/03/index.html)

## 추가 특성

이 Slidy 렉쳐버젼을 사용하면 한 가지 좋은 점은 모든 강의 슬라이드가 자동으로 edit버튼을 얻는다는 것 입니다. 슬라이드의 `edit`버튼을 클릭하면 소스가 열립니다. 이를 통해 사람들은 오타를 바로 잡고 강의 슬라이드에 기여할 수 있습니다.

<a href='lectures/01/#3'>
   <img style='border: 1px solid;' width=100% src=http://www.clipular.com/c?14735047=rpmipgzz3PAoKUVW7jQ4hE30iKk&f=.png></img>
</a>







