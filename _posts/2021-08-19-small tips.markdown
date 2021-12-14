---
layout: post
title: 소소한 CSS 정리
date: 2021-07-19
description: 블로그를 만들면서 찾아봤던 소소한 팁들
img :
---
<br/>

#### SCSS의 $ Variables
Sass 변수. $에 이름을 주고, 값을 할당하면 반복을 줄이고 전체 프로덕트 내의 margin, padding, color, font-family, font-size 등 많은 것들을 일관되게 관리할 수 있다. Figma library의 style과 함께 사용하면 편리하다.

{% highlight scss %}
$title-font-family: 'JosefinSans', 'NotoSansKR', sans-serif;
$base-line-height: 1.7em;
$grey-color-80: #3C3D3F;
$theme-color: #62D9EA;
{% endhighlight %}

<br/>

#### 텍스트 내에 이모지 넣기
텍스트 font-size와 다른 크기의 이모지를 넣고 싶을 때, span 태그 사용. css로 font-size를 설정. 

<span class="emojii">👋</span> 크게 안녕!
<span class="emojiii">👋</span> 더 크게 안녕!
{% highlight html %}
<div class="title"><span class="emoji">👋</span> 디자이너 장종윤입니다.</div>
{% endhighlight %}
{% highlight css %}
emoji {
   font-size: 60px;
}
{% endhighlight %}

<br/>

#### text underline
text-decoration으로 underline을 넣으면, 라인이 글자와 붙어서 가독성과 심미성이 떨어진다. 
text-underline-position: under; 으로 조정.
{% highlight css %}
text {
   text-decoration: solid underline #000000 1px;
   text-underline-position: under;
}
{% endhighlight %}


<br/>

#### 중앙 정렬의 여러 방법
##### 1. text-align: center
보통 텍스트에 사용하지만, img 태그의 부모 요소에 적용할 수 있다.
{% highlight css %}
parent {
   text-align: center;
   width: 100%;
}
{% endhighlight %}

##### 2. position, transform
좌상단 꼭지점을 화면의 중앙에 위치하게 만든 후, 컴포넌트의 width와 height의 절반씩 이동하게 만드는 방법.
{% highlight css %}
div {
   position: absolute;
   top : 50%;
   left : 50%;
   transform: translate(-50%, -50%);
}
{% endhighlight %}

##### 3. margin: auto
컴포넌트의 width를 제외한 좌우 양쪽 여백을 margin 값으로 주는 방법.
{% highlight css %}
div {
   display: block
   margin: auto
}
{% endhighlight %}

<br/>

#### 배경 이미지 background-image
블로그의 포스트에 자주 보이는 상단 이미지처럼, 썸네일 이미지를 해당 영역에 꽉 채워서 넣고 싶을 때는 style background-image를 사용한다.

{% highlight html %}
<div class="header-image"> style="background-image: url( /img/ver2_bookcovery.png );" </div>
{% endhighlight %}
{% highlight css %}
.header-image {
   background-position: center center;
   background-repeat: no-repeat;
   background-size: cover;
}
{% endhighlight %}
