---
layout: page
title: 배포하기
date: May 22 2012
sidebar: false
footer: false
---


옥토프레스 블로그를 깔끔하고 쉽게 배포하는 방법을 소개합니다.


## 깃헙 페이지

블로그를 Github의 [Pages 서비스](pages.github.com)에 호스팅하는건 공짜이고 다른 도메인으로 연결할 수도 있습니다.배포를 하려면 간단히 Github의 저장소에 푸쉬만 하면 됩니다. 이런 점은 개인용 블로그를 운영하기에도 좋고요, pull request와 커밋 방식으로 팀원의 참여가 이루어지는 그룹 블로그 운영하기에도 매우 좋습니다.

[깃헙 페이지(Github Pages)에 배포하기 &raquo;](/octopress/deploying/github)

## Heroku

깃헙 페이지(Github Pages)처럼, Heroku도 공짜입니다. 그리고 다른 도메인을 연결할 수 있고 배포환경은 깃(git)을 기반으로 합니다. Heroku는 깃헙 페이지보다 더 단순하고, 블로그 저장소를 비공개로 관리할 수 있다는 장점이 있습니다.

[Heroku에 배포하기 &raquo;](/octopress/deploying/heroku)

## Rsync

웹 호스팅 서비스를 이용하고 있다면, [Rsync](http://en.wikipedia.org/wiki/Rsync)로 배포할 수도 있습니다. 이렇게 배포하면 SSH를 사용해서 새로운 파일이나 변경된 파일을 동기화시키기 때문에 매우 빠릅니다.

SSH 방식의 접근을 지원하는 웹호스팅 사이트를 찾으신다면, 이 사이트를 살펴 보세요. [Dreamhost](http://www.dreamhost.com/r.cgi?109007) (저는 2005년부터 이 사이트를 쓰고 있는데요, 만족하고 있답니다.)
