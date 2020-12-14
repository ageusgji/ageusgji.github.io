<!--
---
layout: post
title:  "도커 팁!!"
date:   2020-11-17 16:45:03 +0900
categories: docker
---
-->



## docker-compose alias 모음
도커 컴포즈 단축 명령어 등록하기
편의성을 위해 도커 컴포즈를 도입했는데 docker-compose라는 명령어 자체가 너무 길어서 오히려 불편할 수도 있겠죠. 이를 위해 ~/.bashrc나 ~/.zshrc에 다음 내용을 추가합니다.

{% highlight ruby %}
alias dco='docker-compose'
alias dcb='docker-compose build'
alias dce='docker-compose exec'
alias dcps='docker-compose ps'
alias dcr='docker-compose run'
alias dcup='docker-compose up'
alias dcdn='docker-compose down'
alias dcl='docker-compose logs'
alias dclf='docker-compose logs -f'
{% endhighlight %}

이제 docker-compose up 대신 dcup을, docker-compose exec django bash 대신  dce django bash를 실행하면 됩니다.


[[도커 컴포즈 단축 명령어 등록하기 : 원본 링크]](https://www.44bits.io/ko/post/almost-perfect-development-environment-with-docker-and-docker-compose#%EB%8F%84%EC%BB%A4-%EC%BB%B4%ED%8F%AC%EC%A6%88-%EB%8B%A8%EC%B6%95-%EB%AA%85%EB%A0%B9%EC%96%B4-%EB%93%B1%EB%A1%9D%ED%95%98%EA%B8%B0)


-------------------------------------------------------------------------------

## 자동완성 하는 법
Docker 컨테이너의 이름, 이미지 이름은 랜덤으로 생성되는데 터미널에서 자동완성이 되지않아 불편하다. 자동완성이 되게 해보자.


> zsh completion 설치
{% highlight ruby %}
$ brew install zsh-completion
{% endhighlight %}


> docker completion 설치
{% highlight ruby %}
$ brew install docker-completion
{% endhighlight %}

> ~/.zsh/completion/ 폴더를 만들어 파일 복사
{% highlight ruby %}
$ mkdir -p ~/.zsh/completion
$ curl -L https://raw.githubusercontent.com/docker/compose/master/contrib/completion/zsh/_docker-compose > ~/.zsh/completion/_docker-compose
{% endhighlight %}

> ~/.zshrc에 아래 내용 추가
{% highlight ruby %}
## fpath에 경로 추가
fpath=(~/.zsh/completion $fpath)
## compinit 실행
autoload -Uz compinit && compinit -i
{% endhighlight %}

> Shell reload


[[Docker names 자동완성 설정하기 : 원본 링크(http://recordingbetter.com)]](http://recordingbetter.com/aws/2017/07/05/Docker-names-%EC%9E%90%EB%8F%99%EC%99%84%EC%84%B1)
