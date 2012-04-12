---
layout: page
title: Configuring Octopress
date: July 19 2011
sidebar: false
footer: false
---

[&laquo; Previous, Octopress Setup](/octopress/setup)

저는 옥토프레스의 설정을 정말 단순하게 유지하려고 노력했습니다. 여러분은 ‘Rakefile’과 ‘_config.yml’ 파일만 수정하면 됩니다. 옥토프레스 설정관련한 파일은 다음과 같습니다.


``` sh
    _config.yml       # 주요 설정  (지킬 설정)
    Rakefile          # 배포에 관한 설정
    config.rb         # 컴퍼스(Compass) 설정
    config.ru         # 랙(Rack) 설정
```

 `Rakefile`안의 설정들은 대부분 배포에 관련된 것들이며, rsync를 사용하지 않는 이상 건드리지 않아도 됩니다.


## 블로그 환경설정

`_config.yml 파일에는 옥토프레스 블로그 설정에 관한 부분이 세 개의 섹션으로 나누어져 있습니다.

**내용을 미리 조금 이야기하자면...:** `url`은 바꿔야 돼요. 그리고 `title`, `subtitle, `author` 부분도 바꾸고 싶을 겁니다. 그리고 서드 파티 서비스를 사용하도록 설정할 수 있습니다.


### 주요 설정

``` yaml
    url:                # RSS용으로 url을 다시 만들어낼 때 사용합니다.
    title:              # 헤더하고 타이틀 태그에서 사용합니다.
    subtitle:           # 헤더에서 설명하기 위해 사용합니다.(description).
    author:             # RSS, Copyright, 메타데이터에 들어가는 여러분의 이름입니다.
    simple_search:      # 사이트내 검색에 사용할 간단한 검색 엔진입니다.
    description:        # 사이트에 대해 기본으로 제공하는 간단한 메타 설명입니다.
    subscribe_rss:      # 블로그의 피드에 사용하는 Url입니다. 디폴트는 /atom.xml입니다.
    subscribe_email:    # 이메일로 구독하기 위한 url 주소입니다. (서비스가 필요하고요.)
    email:              # RSS피드용으로 사용할 이메일 주소입니다. 원하는 경우에 사용하시면 되요.
```

**주의하세요!** 여러 사람이 쓰는 블로그라면 어쩌면 ‘author’의 값을 당신의 회사나 프로젝트 이름으로 하면 됩니다. 그리고 포스트와 페이지에 실제 작업한 사람을 나타내려면 저자에 대한 메타데이터(author metadata)를 추가하세요.


### 지킬(Jekyll) & 플러그인

여기에 나오는 설정들은 지킬(Jekyll)과 플러그인에서 사용합니다.

지킬 사용이 익숙하지 않으시면, 이곳을 한번 봐주세요. [configuration octopress](https://github.com/mojombo/jekyll/wiki/Configuration)에서, 이 문서에서 다루지 않은 옵션들을 볼 수 있습니다. .


``` yaml
    root:               # 상대 주소(url)를 위한 매핑 (기본값은 : /)
    permalink:          # 블로그 포스트를 위한 퍼머링크 (고유주소) 구조
    source:             # 사이트 소스 파일을 위한 디렉토리
    destination:        # 생성되는 사이트 파일에 대한 디렉토리
    plugins:            # 지킬 플러그인을 위한 디렉토리
    code_dir:           # 코드 스니펫에 대한 디렉토리 (또한 include_code plugin에 대한 디렉토리)
    category_dir:       # 생성되는 블로그 분류 페이지를 위한 카테고리
    pygments:           # pygments 하이라이트 기능을 끄거나 켜기(토글하기)
    paginate:           # 블로그의 인덱스 페이지에서 보여줄 포스트 갯수
    pagination_dir:     # URL에 붙는 페이지의 베이스 경로
    recent_posts:       # 사이드바에서 보여줄 최근 포스트의 개수
    default_asides:     # 사이드바에서 보여줄 것, 보여주는 순서를 설정함
    blog_index_asides:  # 블로그 요약문을 사이드바에 보여줄 지 설정하는 것(Optional sidebar config for blog index page)(블로그 요약문)
    post_asides:        # Optional sidebar config for post layout
    page_asides:        # Optional sidebar config for page layout
```
블로그 포스트의 영구주소(permalinks)가 표기되는 방식을 바꾸고 싶으시면, 이 문서를 보세요.
[지킬의 영구주소 관련문서](https://github.com/mojombo/jekyll/wiki/Permalinks).

**주의하세요!** 지킬에는 WEBrick서버에 연결해서 하위 디랙토리 발행을 구현한 `baseurl` 설정이 있지만  **사용하지 마세요.**

사이트를 하위 디렉토리(subdirectory)로 발행하려면 이 문서를 보세요. [(옥토프레스를 하위 디렉토리에 배포하기)](/octopress/deploying/subdir/).

<h3 id="third_party">써드 파티 설정</h3>

써드 파티를 통합시키기 위한 설정은 이미 준비되어 있습니다. 설정에서 빈 칸을 채우면 사이트에 추가됩니다.

- **트위터** - *트위터 피드 사이드바와 팔로우 버튼, (포스트나 페이지를 공유하는) 트윗버튼을 설정하세요.

- **구글 플러스 원** - *구글 플러스 원 네트워크에서 작성한 포스트와 페이지를 공유하도록 설정하세요.

- **핀보드** - *핀보드에서 즐겨찾기 등록한 것을 블로그의 사이트바에서 보여줍니다.

- **딜리셔스** - *딜리셔스에 최근에 등록한 북마크를 블로그의 사이드바에서 공유하세요..

- **디스커스 댓글** - *사이트에서 disqus를 사용하여 댓글을 달 수 있도록 disqus short name을 여기에 추가하세요.

- **구글 분석기(Google Analytics)** - *구글 분석기로 사이트/블로그를 분석하려면, 여기에 구글 분석기 id를 적어 주세요.

옥토프레스 레아아웃에서는 이 설정사항(configuration)을 읽어들여서, 사용하도록 설정되있고,  서비스에 필요한 자바스크립트와 html만을 포함시킵니다.

[자, 다음은 옥토프레스로 블로깅 하기로 넘어가죠 &raquo;](/octopress/blogging/)
