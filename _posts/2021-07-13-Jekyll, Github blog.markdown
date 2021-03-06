---
layout: post
title:  Jekyll, Github 블로그 만들기
date:   2021-07-13 
description: 개발 환경 구축(설치), 블로그 생성, 커스터마이징
img : /img/github_jekyll_logo.jpg
---
<br/>

### Jekyll이란?
이 블로그는 <a class="post-text" href="https://jekyllrb.com/" target="blank">Jekyll</a>을 사용해 구축했고, 호스팅 플랫폼으로 Github을 사용했다. <a class="post-text" href="https://jekyllrb.com/" target="blank">Jekyll</a>은 Github Pages와 연동되는 site generator 중 하나이다. Jekyll은 Ruby라는 언어를 기반으로 하며, 마크다운 방식으로 글쓰기가 가능하다. 자유롭게 커스터마이징이 가능하며, 마음에 드는 Jekyll theme을 골라 사용할 수도 있다. 이 블로그는 Theme을 Fork하여, 필요한 기능을 추가하고 변경하면서 커스터마이징하였다. 

#### Jekyll 설치를 위해 필요한 것들
<ul>
	<li>Github 계정</li>
	<li><a class="post-text" href="https://brew.sh/" target="blank">Homebrew</a> (최신 버전 Ruby를 동작하기 위해서는 Homebrew를 통해 Ruby를 설치해야 한다.)</li>
	<li>Ruby version 2.5.0 or higher</li>
</ul>

<br/>
<br/>

### Homebrew, Ruby, Jekyll 설치하기
#### 1. Homebrew를 통해 Ruby 설치하기
1.&#160;터미널에 아래 코드를 입력하여 Homebrew를 설치한다.
{% highlight html %}
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
{% endhighlight %}  

2.&#160;터미널에 아래 코드를 입력하여 Homebrew을 통해 Ruby를 설치한다.
{% highlight html %}
$ brew install ruby
{% endhighlight %}

3.&#160;터미널에서 ruby 명령어를 사용하려면 경로를 추가해야 한다. Shell 설정에 ruby와 gems의 경로를 추가하기 전에 먼저 아래 코드로 어떤 Shell을 사용 중인지 확인한다.
{% highlight html %}
echo $SHELL
{% endhighlight %}

- Zsh를 사용 중이라면, 아래 코드로 ruby와 gems의 경로를 추가한다.
{% highlight html %}
echo 'export PATH="/usr/local/opt/ruby/bin:/usr/local/lib/ruby/gems/3.0.0/bin:$PATH"' >> ~/.zshrc
{% endhighlight %}

- Bash를 사용 중이라면, 아래 코드로 ruby와 gems의 경로를 추가한다.
{% highlight html %}
echo 'export PATH="/usr/local/opt/ruby/bin:/usr/local/lib/ruby/gems/3.0.0/bin:$PATH"' >> ~/.bash_profile
{% endhighlight %}

4.&#160;Ruby와 gem이 잘 설치되었는지 확인한다. (Ruby 버전은 2.5.0 이상이어야 한다.)
{% highlight html %}
$ ruby -v
$ gem -v
{% endhighlight %}


#### 2. Jekyll 설치하기
1.&#160;ruby와 gem이 잘 설치된 것을 확인했다면, gem을 통해 jekyll을 설치한다.
{% highlight html %}
$ gem install jekyll bundler
{% endhighlight %}

2.&#160;Jekyll이 잘 설치되었는지 확인한다.
{% highlight html %}
$ jekyll -v
{% endhighlight %}
<br/>
<br/>

### Github Blog 만들기
1.&#160;github에서 새로운 Repository를 만든다.

2.&#160;Repository의 이름은 반드시 username.github.io로 설정해야한다. Repository의 이름이 username과 다르면 작동하지 않을 수 있으니 유의한다.  

3.&#160;Github의 repository를 로컬 디렉토리와 연결하는 방법에는 두가지가 있다. 하나는 github repository의 파일들을 로컬로 clone(다운로드)해오는 것이고, 두번째는 로컬 디렉토리의 파일들을 github repository에 올려서 연결하는 방법이다.   
 - 터미널에서 github repo를 clone할 디렉토리(빈 폴더)로 이동한 후 아래 코드를 입력해 clone한다.
{% highlight html %}
git clone 나의 repository URL
{% endhighlight %}

- 터미널에서 github repo에 올리고 싶은 디렉토리로 이동한 후 git을 실행시켜 repo와 연결한다.
{% highlight html %}
$ git init
$ git remote add origin 나의 repository URL
{% endhighlight %}

4.&#160;연결이 되었다면, 첫번째 commit을 해보자.
{% highlight html %}
$ git add *
$ git commit -m "First commit"
$ git push -u origin main(또는 master, 이는 자신의 마스터브랜치 이름이다.)
{% endhighlight %}

5.&#160;push가 성공적으로 되었다면, 로컬 폴더의 파일들이 github repository에 업데이트된 것을 확인할 수 있을 것이다. 혹은 반대.

<br/>
<br/>

### Jekyll Theme 
#### Jekyll theme 고르기

Jekyll theme은 구글링을 통해 쉽게 찾을 수 있다. 유료와 무료 다양한 옵션들이 있다.
- <a class="post-text" href="https://jekyllthemes.io/" target="blank">jekyllthemes.io</a>
- <a class="post-text" href="http://jekyllthemes.org/" target="blank">jekyllthemes.org</a>

Jekyll의 가장 주요한 장점이 자유로운 커스터마이징이 가능하다는 것인데, 어차피 커스터마이징을 할 거라면 만들고자 하는 사이트의 구조를 먼저 생각하고 디자인보다는 원하는 구조에 가까운 theme으로 선택하는 것이 좋다. 나는 개발 관련 정리를 할 수 있는 Blog와 포트폴리오를 합친 형태를 기획했고, 블로그와 포트폴리오를 합친 구조의 다양한 theme 옵션들 중에서 Blog와 구분된 가벼운 기록 글들을 올릴 수 있는 것이 마음에 들어 *folio라는 theme을 선택했다. 

#### Jekyll theme 적용하기
원하는 theme을 골라 다운로드 받았다면, 선택한 theme의 파일들을 모두 프로젝트 디렉토리(폴더)로 복붙하고 push하면 된다.
{% highlight html %}
$ git add *
$ git commit -m 'theme change'
$ git push -u origin main
{% endhighlight %}

<br/>
<br/>

### Jekyll 커스터마이징
#### Jekyll의 기본 directory
##### _config.yml	
환경 설정 변수를 정의한다. 페이지네이션, 빌드 세팅 및 사이트의 이름, description, url 등 메타 정보를 정의한다.  
##### _includes	
head, header, footer의 사이트 전반에 공통으로(반복적으로) 사용되는 HTML 파일을 관리한다. <code>&#123;% include file.ext %&#125;</code> 와 같이 Liquid 태그를 사용하면 <code>&#95;includes/file&#46;ext</code> 파일에 담긴 코드가 삽입된다.  
##### _layouts	
post, page 등 페이지의 레이아웃을 정의하는 HTML 파일을 관리한다. default.html 문서에 _includes에서 정의한 html이 liquid 태그로 쓰여있다.  
##### index.md	
Index 페이지(사이트 진입시 첫 페이지)를 정의한다.  
##### _sass	
SCSS 파일이 모여져 있는 곳이다.  
##### _posts	
포스트 마크다운(컨텐츠)을 관리한다.
##### _drafts	
아직 배포하지 않은 draft posts를 담고 있다.

#### 첫 진입 페이지 변경하기


<br/>
<br/>

### 기타 Memo
##### 로컬 서버 호스트
bundle exec jekyll serve  
로컬 서버를 종료하려면, ctrl+c

##### push하기  
git add &#42; : all  
git add &#42;.scss : 모든 scss 파일  
git add a_&#42;.txt : a_1부터 a_n의 모든 txt 파일)  
git add 특정 파일 이름 : 해당 파일만

##### terminal 명령어  
cd : change directory  
ls : list directory contents)  
cd 원하는 경로명+tab 또는 원하는 경로명/ : 해당 경로로 이동


