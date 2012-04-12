---
layout: page
title: 옥토프레스 설정하기
date: May 22 2012
sidebar: false
footer: false
---

먼저, **옥토프레스는 해커들을 위한 블로그 프레임워크**라는 점을 강조하고 싶어요.
옥토프레스를 쓰시려면 Git 기본 사용법이 익숙해야 하고,
쉘 커맨드에서 편하게 명령어를 실행할 수 있어야 해요.
이 말이 어렵게 느껴진다면, 옥토프레스는 아마 힘드실 거에요.

## 시작하기 전에

옥토프레스로 블로깅을 하려면 우선은 [깃(Git)을 설치](http://git-scm.com/)해야 합니다. 그리고 루비를 설치해야 해요.
** 옥토프레스를 쓰려면 루비 1.9.2가 필요합니다** [RVM](http://rvm.beginrescueend.com) 이나 [rbenv](https://github.com/sstephenson/rbenv)를 사용하면 쉽게 루비 1.9.2를 설치할 수 있어요.


rbenv 와 RVM은 루비 환경 관리툴인데요, 동시에 사용하면 충돌하므로, 하나만 선택해 주세요.

### RVM을 사용하실 경우

아직 RVM을 사용하지 않으시면, [RVM을 설치하시고](/octopress/setup/rvm)  루비 1.9.2를 설치해주세요.

```sh
rvm install 1.9.2 && rvm use 1.9.2
```

### rbenv를 사용하실 경우


아직 rbenv를 사용하지 않으시면, [rbenv를 설치하시고](https://github.com/sstephenson/rbenv#section_2) [ruby-build를 설치 하시고](https://github.com/sstephenson/ruby-build) 루비 1.9.2를 설치해주세요.

```sh
rbenv install 1.9.2-p290
```

## 옥토 프레스 설정하기


```sh
git clone git://github.com/imathis/octopress.git octopress
cd octopress    # RVM를 사용하시면, .rvmrc 파일을 신뢰하는지 묻는 선택지가 나옵니다 (yes 라고 입력해주세요).
ruby --version  # 1.9.2버전이어야합니다.
```

만약 `ruby --version`해서 1.9.2이외의 버전이 나오면, [RVM 설치하기](/octopress/setup/rvm)부분을 보면서 다시 설치해주세요.

이제 의존라이브러리를 설치합시다.


```sh
gem install bundler
rbenv rehash    # rbenv를 사용하신다면, rehash 명령을 실행해서 bundle 명령이 실행되도록 합시다.(*역주:RVM 을 사용하신다면 이 부분은 건너뛰어도 됩니다.)
bundle install
```

기본 테마를 설치합시다.


``` sh
rake install
```

## 다음 단계

- [배포하기](/octopress/deploying)
- [블로그 설정하기](/octopress/configuring)
- [옥토프레스로 블로깅 시작하기](/octopress/blogging)
