---
layout: page
title: 블로깅하기 기본편
date: July 19 2011
sidebar: false
comments: false
footer: false
---


옥토프레스에서는 rake task를 몇 개 제공합니다. 이를 사용해서 메타데이터가 로드된, 그리고 지킬의 명명 규칙에  따르는 포스트와 페이지를 만들 수 있습니다.

또한 옥토프레스에서는 포스트에 대한 전체 피드, 카테고리별 피드를 생성합니다. ( `atom.xml`와,  `blog/categories/<category>/atom.xml`에서 확인할 수 있습니다).

## 블로그 글쓰기

블로그 글은 `source/_posts`디랙토리 밑에 저장 되고 지킬(Jekyll)의 이름 규칙(`YYYY-MM-DD-post-title.markdown`)을 따라야 합니다. 파일의 이름은 url의 일부로 이용되고 날짜는 글들을 구분하고 보여주는 순서를 정하는데 사용됩니다.

옥토프레스에서는 rake 명령어를 제공하는데요, rake 명령어를 사용하면 정확한 명명 규칙을 따르며 적절한 yaml 메타데이터를 포함하는 새 블로그 포스트를 만들 수 있습니다.


#### 문법 (Syntax)

``` sh
    rake new_post["title"]
```

`new_post` 명령어의 뒤에는 자연스러운 제목이 와야 합니다.그리고 `new_post`는 파일이름을 만들 때, url로 쓰기에 부적합한 문자는 제거해 줍니다.

새로운 포스트의 기본 확장자는 `markdown` 이지만 `Rakefile` 에서 수정할 수 있습니다.

#### 새로운 포스트를 만드는 방법 - 예


``` sh
    rake new_post["Zombie Ninjas Attack: A survivor's retrospective"]
   # (닌자 좀비의 공격 : 살아남은 자의 회상)
    # 이렇게 쓰면 다음의 파일이 만들어집니다. source/_posts/2011-07-03-zombie-ninjas-attack-a-survivors-retrospective.markdown
```

파일이름에 따라서 url 주소가 만들어집니다. 위에서 만든 포스트의 기본url은 이렇습니다. `http://site.com/blog/2011/07/03/zombie-ninjas-attack-a-survivors-retrospective/index.html` [기본 영구주소 설정에 관하여] (https://github.com/mojombo/jekyll/wiki/Permalinks)


포스트를 텍스트 편집기에서 열어서 보세요. 포스트와 페이지를 처리하는 방법을 알려주는 yaml 부분 [yaml front matter](https://github.com/mojombo/jekyll/wiki/yaml-front-matter)을 볼 수 있을 겁니다.

``` yaml
    ---
    layout: post
    title: "Zombie Ninjas Attack: A survivor's retrospective"
    date: 2011-07-03 5:59
    comments: true
    categories:
    ---
```

여기서는 댓글 기능을 숨기거나 포스트의 카테고리를 지정할 수 있습니다. 팀블로그를 운영하신다고요? 그렇다면 포스트의 메타데이터에 `author: 저자의 이름`를 추가하면 됩니다. 초안 작업 중이라면, 포스트의 메타데이터에 `published: false`라고 추가해두면, 포스트를 저장하더라도 블로그에 게시되지 않습니다.

카테고리를 한 개, 또는 여러 개 추가하려면, 아래와 같이 하세요.

``` yaml
     # 카테고리 한 개 추가하는 방법
    categories: Sass

    # 카테고리 여러 개 추가하는 방법 - 1
    categories: [CSS3, Sass, Media Queries]

    # 카테고리 여러 개 추가하는 방법 - 2
    categories:
    - CSS3
    - Sass
    - Media Queries
```
## 새로운 페이지 만들기

블로그 소스 폴더에다가 페이지를 만들어두면 지킬이 파싱을 해줍니다.

그리고 파일의 경로에 따라 URL이 만들어져요.
즉, `about.markdown` 파일을 만들면, 이 페이지의 URL은 `site.com/about.html`이 됩니다.
`site.come/about/` 이런 경로를 쓰고 싶으시면, 페이지를 만드실 때 `about/index.markdown` 이렇게 about 폴더 안에 만들면 됩니다.

옥토프레스에서는 rake 명령어를 사용해서 새로운 페이지를 쉽게 만들 수 있습니다.

``` sh
    rake new_page[super-awesome]
    # 이렇게 써주면 /source/super-awesome/index.markdown 파일이 만들어집니다.

    rake new_page[super-awesome/page.html]
    # 이렇게 써주면 /source/super-awesome/page.html 파일이 만들어집니다.
```

new post 명령어를 썼을 때와 마찬가지로, 새로운 페이지 파일의 기본 파일확장자는 `markdown`이지만, `Rakefile`에서 수정할 수 있습니다. 새로 생성된 페이지를 편집기에서 열어보면 다음과 같이 나옵니다.


``` yaml
    ---
    layout: page
    title: "Super Awesome"
    date: 2011-07-03 5:59
    comments: true
    sharing: true
    footer: true
    ---
```

포스트의 제목은 파일명에서 자동으로 추출됩니다. 그러니, 포스트의 제목은 별도로 바꿔줘야 합니다.

이것은 yaml 포스트하고 매우 비슷합니다. 카테고리를 포함하지 않는다는 점만 빼면요. 그리고 공개/비공개 여부를 바꿀 수도 있고, footer 부분을 모두 제거할 수도 있습니다.

페이지에서 날짜 부분을 안 보여주고 싶으면, yaml에서 지워버리면 됩니다.

## 페이지, 포스트의 내용부분(Content)

페이지 및 포스트의 내용부분(content)은 여러분이 사이트 환경 파일(site configuration file)에서 지정해둔 마크업 엔진에 의해 표현됩니다(render).

또한 지킬문서 [Jekyll docs](https://github.com/mojombo/jekyll/wiki/Template-Data) 에서 소개하는 리퀴드 템플릿 기능 [liquid template features](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) 을 사용할 수 있습니다.

포스트에다가 주석(`<!-- more -->` )을 포함시키면, 주석표시 아래의 부분은 요약문(index page)에 안 나옵니다. 대신에 "Continue →" 버튼이 나옵니다. 이 버튼을 누르면 전체 포스트를 볼 수 있습니다.

## 새로운 포스트 만들기 & 미리보기


``` sh
    rake generate   # public 폴더 안에 새로운 포스트와 페이지를 만듭니다.
    rake watch      # source/나 sass/ 폴더 안에 변경된 것이나 새로 생성된 것이 있는지 감시(watch)합니다.
    rake preview    # 감시하고 웹서버를 http://localhost:4000에다가 마운트합니다.
   (역자주 : 감시(watch) : 변경사항이 있으면 자동으로 html이나 css를 생성해주는 명령어)
```

포스트를 발행하지 않은 채로 작업하려면, 포스트의 YAML 헤더 부분에 `published:false`를 추가하면 됩니다.

이 상태에서 `rake preview` 명령어를 사용하면 로컬 서버에서 이 포스트를 미리 볼 수 있습니다. 하지만 `rake generate` 명령어를 사용해도 포스트는 발행되지 않습니다.

‘rake preview’ 서버를 사용하는 것은 멋지지만 여러분이 [POW](http://pow.cx) 사용자라면, 옥토프레스 사이트를 다음과 같이 설정할 수 있습니다.
``` sh
    cd ~/.pow
    ln -s /path/to/octopress octopress
    cd -
```

자~ 이제 POW를 설정했으니, `rake watch`를 실행해서, http://octopress.dev를 로드해보세요. (역자주: POW - 자동화툴의 하나)

그리고 [코드조각 공유하기](/octopress/blogging/code)하고 [플러그인 사용해서 블로깅하기](/octopress/blogging/plugins)문서도 봐 주세요.
