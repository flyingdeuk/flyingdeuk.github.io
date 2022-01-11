---
title: Github Pages - The page build failed for the `gh-pages` branch with the following error 해결법
date: 2021-07-29
categories: [Coding, Github]
tags: [github, usefulsite]
pin:
---

![pages](/img/coding/github/pages.jpg)

`FlyingDeuk's`
> Github Pages는 정적인 블로그 공간을 제공하지만 일부 프로그램에 대해서는 조금씩 제한을 두는 분위기이다. <br>
jekyll은 ruby를 베이스로 한다는 데.... error가...

## Github Pages error 해결법
얼마전 일상적으로 블로그를 작성해서 올리는 데 아래와 같은 메세지를 메일로 받았다.
> 당황했다. 더이상 공식 Github 인증 Theme가 아니면 안되는 건가 어디로 이사를 가야하나...


The page build failed for the `gh-pages` branch with the following error: <br>
The primer theme is not currently supported on GitHub Pages. For more information, see https://docs.github.com/github/working-with-github-pages/adding-a-theme-to-your-github-pages-site-using-jekyll.


구글링 결과 2가지 정도의 해결방법이 있었다.

1. _config.yml -> theme 변수 주석 처리

  ```
  #theme: [Any theme name on above link]
  ```
  >theme 부분을 #으로 주석으로 처리한다.

2. _config.yml -> theme 변수 값 수정

  <https://pages.github.com/themes/>  공식 Theme중 하나로 변경

  ```
  theme: [Any theme name on above link]
  ```
  >theme는 다르지만 공식 theme 이름으로 변경해준다.

------

### PostScript

Github에서는 몰라야 할 텐데...
