---
title: jekyll 블로그 만들기 (번외)
author: aa
categories: [Blog, jekyll]
date: 2022-10-07 19:05:00 +0900
tags: [jekyll, github, blog, github-desktop, error]
---

# 깃 설치와 오류

---

저번 글에서 환경 구축이라고 해놓고서 git 설치를 빼먹었네요 ㅎㅎ

간단하게 짚고 넘어가겠습니다. github를 이용한 블로그 만들기라서 `git`이 없으면 안됩니다.

설치하는 방법이 두 가지 있습니다. 하나는 **CLI**, **GUI**. 즉 터미널을 이용하는 방법과 프로그램을 통해 이용하는 방법이 있습니다. 터미널 사용이 익숙하지 않으신 분은 GUI를 이용하시면 편합니다.

또한 Xcode가 이미 설치되어 있는 분은 기본적으로 git이 설치되어 있을겁니다. 확인 방법은 `git --version`을 입력하여 확인해보시면 됩니다.

# 깃 설치

---

## CLI 인스톨

---

먼저 터미널을 열고, `brew install git`을 입력하시면 됩니다. 또는 **Xcode**를 설치하시면 자동으로 설치됩니다.

이후 `git --version` 명령어를 통해 정상적으로 설치되었는지 확인하시면 됩니다.

![1-1](/assets/img/img/22-10/10-07/1-1.png)
*터미널 화면*

## GUI 인스톨

---

GUI 버전은 깃허브 홈페이지에서 다운로드 받으실 수 있습니다. 또는 [이 곳](https://desktop.github.com)에 접속하여 **Download for macOS**를 눌러 받으시면 됩니다. 

저는 이미 설치되어 있고 사용하는 중이라 사진이 조금 다를 수도 있습니다.

![github dsektop](/assets/img/img/22-10/10-07/1-2.png)
*GitHub Desktop 메인화면*

# GitHub Desktop

---

## 초기설정

---

처음 프로그램을 실행하게 된다면 위 화면과 비슷하게 나올겁니다. 우선 깃을 설치해줄 필요가 있는데, 위에서 터미널로 설치하신 분들은 넘어가셔도 됩니다.

![깃허브 로그인](/assets/img/img/22-10/10-07/1-3.png)

사진처럼 애플 아이콘 옆에 **“GitHub Desktop”**을 누르고 **“Preferences…”**를 누르셔도 되고, 단축키 `command + ,`를 눌러 설정화면으로 진입합니다.

![설정창](/assets/img/img/22-10/10-07/1-4.png)
*GitHub Enterprise가 아닌 GitHub.com을 로그인해줍시다.*

설정으로 들어가게 되면 위 사진처럼 로그인 탭이 제일 먼저 나오게 되는데 **Sign In**을 눌러 GitHub와 연동해줍시다.

---

이후 user name과 user email 설정을 해줄 필요가 있습니다. **GitHub Desktop**을 활용하는 경우에는 필요없지만 터미널로 작업하는 경우 누가 커밋을 했는지 알아야 하기 때문에 등록해줘야 합니다.

설정은 **전역 설정**과 **로컬 설정**이 있는데 특별한 경우가 아니면 전역 설정만 하셔도 됩니다. 참고로 로컬 설정은 로컬 리포지토리 하나를 지정해 그것에 대한 이름과 이메일 설정하는 것입니다.

```terminal
#전역 설정
git config --global user.name "username"
git config --global user.email "useremail"
#로컬 설정
cd enter/your/path
git config --local user.name "username"
git config --local user.email "useremail"
```



# 오류 해결

---

처음 이 블로그 하나를 만들어보겠다고 맨땅에 헤딩하며 해보았는데, 다행히 템플릿 같은게 잘 되어있어서 감사(?)하게도 수고는 덜었죠. **하지만** 이미 완성된 템플릿을 가지고 만드는 것임에도 불구하고 오류는 체감상 무슨 개발하는 정도로 마주해야 했습니다.

물론 아무것도 모르는 백지 상태인데 무지성으로 만든게 한 몫 했습니다. ㅎㅎ

제가 경험한 오류들을 정리해서 올려드리면 여러분은 그나마 하시기 쉽지 않을까 라는 생각에 끄적여 봅니다.

처음 만들 때만해도 본 오류가 수가지 되는데 막상 다 고치고 나니까 기억이 잘 안나네요 ㅎㅎ



## source ~/.zshrc

---

zshrc 파일을 수정하고 `source`를 통해 새로고침 하는 도중 **“parse error near”**이러한 에러가 발생한 경우 vi 편집기를 통해 zshrc를 수정하는 중 오타가 났을 확률이 높습니다

따라서 손수 타이핑 하신 분들은 복사+붙여넣기를 해보시고, 그래도 안되시는 분들은 검색창에 “rbenv zshrc”라고 검색하시고 다른 문장을 넣어보시는게 좋을 거 같습니다.



## error ‘/’ not found

---

`bundle exec jekyll serve`를 통해 로컬 서버로 사이트에 접속했을 때 나오는 오류 중 하나 입니다.

해당 오류는 직접적인 문제는 없지만 상당히 거슬리고, 실제로 사이트를 만들었을 경우 다른 오류를 낼 수 있으므로 고치는게 좋습니다. 

해결 방법은 리포지토리 안에 존재하는 `_config.yml`을 수정하는 것으로 가능합니다. 이 문제는 baseurl 또는 url에 `/`를 넣어놓은 상태일 확률이 높은데 해당 주소를 블로그 주소로 바꿔주신다면 더 이상 오류가 나오지 않을겁니다.

특히 baseurl 부분은 잘 모르신다면 공백으로 두시는게 좋습니다.

```yml
url: 'https://username.github.io'
baseurl: ''
```



## 깃허브 push 오류

---

변경된 내용을 커밋하고 push 한 후 깃허브 사이트에서 커밋 내용을 확인하였을 때 X 표시와 함께 push가 정상적으로 이루어지지 않는 경우가 있습니다. 

구체적으로 어떤 상황이었는지 기억은 나지 않지만 그 때 당시 제가 했던 방법을 나열해드리겠습니다.



### .gitignore

---

바보같이 Gemfile.lock을 커밋 무시 지정해준다고 생각해놓고 안해놓은 놈입니다…

해당 문제와 관련이 있는지 없는지 자세하게는 생각이 안나지만, 이 녀석이 커밋될 경우 문제를 일으킬 위험이 큰 녀석이라 지정 안해놓으셨다면 해놓으시는걸 추천드립니다.

.gitignore 파일을 열고 맨 아랫줄에 `Gemfile.lock` 한 문장만 넣어주면 끝납니다.



### pages-deploy.yml

---

이 방법은 정석인 방법인지 확인은 못했지만 이 녀석이 도움이 된거 같아서 올립니다.

로컬 리포지토리 내부 경로 .github/workflows 안에 있는 pages-deploy.yml을 열어 줍시다.

```yaml
name: "Build and Deploy"
on:
  push:
    branches:
    #이 부분에 자신이 사용하는 브렌치 이름을 적어줍시다.
      - main
      - master
    paths-ignore:
      - .gitignore
      - README.md
      - LICENSE
  
```

```yaml
- name: Setup Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: 3.0.4
          #루비 버전을 자신이 현재 사용하는 루비 버전으로 맞춰줍시다.
          bundler-cache: true
```





## can not load such File – webrick

---

해당 문제 또한 로컬 서버로 사이트에 접속하려 할 때 발생하는 문제로 한 번 수정해놓으면 테마를 바꾸지 않는 한 다신 못볼 오류입니다.

`bundle add webrick`을 먼저 한 번만 입력해주시고 `bundle exec jekyll serve`를 입력해주시면 됩니다.

여기에 없는 오류는 `bundle exec jekyll serve --trace`를 입력해 무슨 문제인지 확인 후 검색하시면 어지간한 문제는 다 나와있으니 참고해주세요!
