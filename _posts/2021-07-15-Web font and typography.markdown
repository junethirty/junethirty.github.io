---
layout: post
title: 웹폰트 및 타이포그래피
date: 2021-07-15
description: Web font 적용 및 최적화, Code memo
---
<br/>

### 웹폰트 적용

웹폰트 적용에는 @font-face를 사용한다. font-family로 서체의 이름(파일명이 아니다)을 지정하고, weight나 style별로 @font-face를 복수 사용하여 필요한 서체를 적용한다.

{% highlight css %}
@font-face {
    font-family: 'Montserrat';
    src: url('/fonts/Montserrat-Bold.woff2') format('woff2'),
        url('/fonts/Montserrat-Bold.woff') format('woff'),
        url('/fonts/Montserrat-Bold.ttf') format('truetype');
    font-weight: 800;
    font-style: normal;
    font-display: swap;
}
{% endhighlight %}

<br/>
<br/>

### 웹폰트 최적화 

#### 1. 폰트 파일 용량 최적화
##### 웹폰트 형식
서체 파일의 형식은 용량(크기)이나 호환되는 브라우저 등 각기 다른 속성을 가지고 있다. 디자인 작업을 할 때는 고해상도 출력이 가능한 OTF 파일 형식을 주로 사용하지만, 웹에서는 서체 적용에 다운로드 시간이 걸리므로 용량을 고려해야 한다. 또한 파일 형식에 따라서 브라우저별 지원 여부가 다르기 때문에 이에 대비해서 대응하는 것이 필요하다.

용량과 호환 브라우저를 고려하여, WOFF2, WOFF, TTF까지 세가지를 대응한다. 

서체 형식 변환시 <a class="post-text" href="https://transfonter.org/" target="blank">Transfonter</a>를 이용했다. <a class="post-text" href="https://transfonter.org/" target="blank">Transfonter</a>는 서체 복수개를 업로드한 뒤 TTF, WOFF2, WOFF, EOT, SVG 중 원하는 형식으로 한번에 컨버트할 수 있고, 하나의 폴더로 다운로드되어 편리하다. 컨버트시 CSS Stylesheet를 함께 제공한다.

##### Google Fonts
<a class="post-text" href="https://fonts.google.com/" target="blank">Google Fonts</a>를 이용하면 font file을 별도로 올리지 않아도 유저 접속시 <a class="post-text" href="https://fonts.google.com/" target="blank">Google Fonts</a>에서 서체를 바로 다운로드 받아 적용할 수 있다. Google Fonts에서 제공하는 link 또는 @import와 CSS 코드를 적용하면 된다. font file을 별도로 올리지 않으므로 용량을 차지하지 않는다는 장점이 있다.

#### 2. 웹폰트 로딩시 텍스트 처리(CSS font-display)
font file을 직접 올리든, Google Fonts에서 받아오든 유저의 사이트 접속시 해당 서체가 다운로드되어야 하기 때문에, 서체가 제대로 적용되기까지의 렌더링에는 일정 시간이 소요될 수 밖에 없다. 대부분의 사이트에서 텍스트가 잠깐동안 반짝하는 현상이 일어나는 것도 서체가 적용되기까지 시간차가 있기 때문이다. 서체가 로딩되기 전까지 텍스트를 어떻게 처리할 것인지는 처리 방식에 따라 달라지는데, 아예 보여주지 않는 경우 경우에 따라서 잘못된 정보를 전달할 위험이 있다. 따라서 텍스트 처리 방식을 적절히 적용하여 최적화를 해야한다.

CSS의 <a class="post-text" href="https://developer.mozilla.org/ko/docs/Web/CSS/@font-face/font-display" target="blank">font-display</a>로 웹폰트의 로딩 상태에 따라 텍스트가 어떻게 보일지를 설정할 수 있다. <a class="post-text" href="https://developer.mozilla.org/ko/docs/Web/CSS/@font-face/font-display" target="blank">font-display</a>는 Internet Explorer 계열 브라우저를 제외한 브라우저가 지원한다. font-display에는 auto, block, swap, fallback, optional의 다섯 가지 옵션이 있다.

##### block 
FOIT(Flash Of Invisible Text: 브라우저 렌더링 차단 방식)와 동일하게 폰트가 로딩되기 전까지 텍스트를 보여주지 않는다(3초까지, 이후에는 폴백 폰트 적용).  

##### swap 
FOUT(Flash Of Unstyled Text)와 동일하게 폰트가 로딩되지 않았다면, 로딩이 완료될 때까지 우선 폴백 폰트로 텍스트를 렌더링하다가 로딩이 완료되면 서체를 적용한다. 따라서 로딩 여부와 관계없이 텍스트가 보인다는 장점이 있다.

##### fallback
block처럼 0.1초까지 폰트가 로딩되지 않았다면 텍스트를 보여주지 않다가, 이후 폴백 폰트를 적용한다. 약 3초까지는 (swap과 마찬가지로) 로딩이 완료될 때까지 우선 폴백 폰트로 대체하고 로딩이 완료되면 웹폰트로 텍스트를 렌더링한다. 하지만 이 시간이 지난 후에는 로딩 여부와 관계없이 계속 폴백 폰트를 유지한다. 로딩이 완료되었다면 페이지를 벗어나거나 재접속한 경우 캐시에 저장된 폰트가 렌더링된다.

##### optional
fallback과 비슷하게 0.1초까지 텍스트를 보여주지 않다가, 이후 폴백 폰트를 적용한다. 하지만 페이지를 벗어나거나 재접속한 경우 캐시에 저장된 폰트가 렌더링되는 fallback과는 달리, 네트워크 연결이 너무 느린 경우 계속 폴백 폰트를 적용한다. 


<br/>
<br/>


### 섞어쓰기 

유료 서체가 아닌 경우에 쓸만한 국영문 혼용 서체의 선택지는 많지 않다. 보통 노토산스나 노토산스를 기반으로 만든 스포카산스를 주로 사용하는데, Open Font License를 가진 대부분의 서체들은 영문 등 하나의 언어만을 지원하는 경우가 많기 때문에, 서체로 아이덴티티를 보여주어야 하거나 특별한 서체를 사용하고 싶은 많은 경우에 영문과 한글 서체 섞어쓰기가 필요하다. 


#### 1. unicode-range 사용  

@font-face에 unicode-range를 사용하면 서체에서 사용되는 유니 코드의 범위를 설정할 수 있다. 서체에 원하는 유니코드 범위(예컨대 영문, 한글, 숫자, 기호 등)를 적용하면, 서체 섞어쓰기가 가능하다.

{% highlight css %}
@font-face {
    font-family: 'Montserrat';
    font-size: 16px;
    font-weight: 300;
    /* 영문 대문자, 영문 소문자, 숫자에만 적용하는 unicode-range */
    unicode-range: U+0041-005A, U+0061-007A, U+0030-0039;
}

{% endhighlight %}

#### 2. 유니코드 범위
영문 범위 (대문자) : U+0041-005A  
영문 범위 (소문자) : U+0061-007A  
한글 : U+AC00-D7AF  
숫자 : U+0030-0039  
  
  
