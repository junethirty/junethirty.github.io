---
layout: post
title: CSS, SCSS, SASS
date: 2021-07-18
description: 개념, Syntax 예시
img : /img/sass_logo.jpg
---
<br/>

### 개념 
CSS : Cascading Style Sheets  
SCSS : Sassy CSS  
<a class="post-text" href="https://sass-lang.com/" target="blank">SASS</a> : Syntactically Awesome Style Sheets  

SCSS와 <a class="post-text" href="https://sass-lang.com/" target="blank">SASS</a>는 CSS를 보완하는 확장 스크립트 언어이다. 문법이나 구문이 조금씩 다르다. 유지보수의 편의성 등 CSS의 한계를 보완하기 위해 조건문이나 반복문, variable(변수), mixin, nesting 등 개념이 추가되었다. SASS보다는 SCSS의 사용이 (공식 문법의 기준, CSS와의 호환성, 다수의 사용자 등의 이유로) 권장된다.

<br/>
<br/>

### Syntax 예시
CSS

{% highlight css %}
nav {
 color : blue;
}
nav ul {
 margin: auto;
}
nav li {
 list-style: none;
 float: left;
}
{% endhighlight %}

SCSS  

{% highlight scss %}
nav {
 ul {
  margin: auto;
 }
 li {
  list-style: none;
  float: left;
 }
}
{% endhighlight %}

SASS 
{% highlight sass %}
nav 
 ul 
  margin: auto;
 li 
  list-style: none;
  float: left;
{% endhighlight %}

<blockquote>
	...
</blockquote>



<!--
---
layout: post
title:  a post with images
date: 2015-05-15
description: this is what included images could look like
---
Jean shorts raw denim Vice normcore, art party High Life PBR skateboard stumptown vinyl kitsch. Fingerstache four loko meh 8-bit, tousled banh mi tilde forage Schlitz dreamcatcher twee 3 wolf moon. Chambray asymmetrical paleo salvia, sartorial umami four loko master cleanse drinking vinegar brunch. 

<div class="img_row">
	<img class="col three" src="/img/9.jpg">
</div>
<div class="img_row">
	<img class="col three" src="{{ site.baseurl }}/img/9.jpg">
</div>
<div class="col three caption">
	A simple, elegant caption looks good between image rows, after each row, or doesn't have to be there at all. 
</div>
<div class="img_row">
	<img class="col two" src="/img/8.jpg">
	<img class="col one" src="/img/10.jpg">
</div>

Slow-carb four dollar toast Helvetica pop-up. Kale chips next level literally trust fund Pitchfork. Jean shorts Pinterest beard, farm-to-table irony craft beer swag tofu 8-bit Banksy. Quinoa forage fanny pack, pug hashtag Echo Park heirloom Schlitz tote bag artisan Neutra mumblecore 90's shabby chic raw denim.


<div class="img_row">
	<img class="col one" src="/img/11.jpg">
	<img class="col one" src="/img/12.jpg">
	<img class="col one" src="/img/7.jpg">
</div>
-->