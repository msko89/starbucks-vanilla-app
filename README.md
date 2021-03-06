## Starbucks Vanilla App Clone

# favicon.ico

- Project Root 경로에 있으면 자동 설정
- favicon.png 사용하고 싶으면 index.html에 설정

```html
<link rel="icon" href="./favicon.png" />
```

- .ico 파일 제작
  - 이미지를 업로드하면 손쉽게 .ico 파일을 제작할 수 있습니다.
  - iconifier.net

# 오픈 그래프(The Open Graph protocol)

- 웹페이지가 소셜 미디어로 공유될 때 우선적으로 활용되는 정보를 지정
  - og:type: 페이지의 유형(E.g, website, video.movie)
  - og:site_name: 속한 사이트의 이름
  - og:title: 페이지의 이름(제목)
  - og:description: 페이지의 간단한 설명
  - og:image: 페이지의 대표 이미지 주소(URL)
  - og:url: 페이지 주소(URL)

```html
<meta property="og:type" content="website" />
<meta property="og:site_name" content="Starbucks" />
<meta property="og:title" content="Starbucks Coffee Korea" />
<meta
  property="og:description"
  content="스타벅스는 세계에서 가장 큰 다국적 커피 전문점으로, 64개국에서 총 23,187개의 매점을 운영하고 있습니다."
/>
<meta property="og:image" content="./images/starbucks_seo.jpg" />
<meta property="og:url" content="https://starbucks.co.kr" />
```

# 트위터 카드(Twitter Cards)

- 웹페이지가 트위터로 공유될 때 우선적으로 활용되는 정보를 지정
  - twitter:card: 페이지(카드)의 유형(E.g. summary, player)
  - twitter:site: 속한 사이트의 이름
  - twitter:title: 페이지의 이름(제목)
  - twitter:description: 페이지의 간단한 설명
  - twitter:image: 페이지의 대표 이미지 주소(URL)
  - twitter:url: 페이지 주소(URL)

```html
<meta property="twitter:card" content="summary" />
<meta property="twitter:site" content="Starbucks" />
<meta property="twitter:title" content="Starbucks Coffee Korea" />
<meta
  property="twitter:description"
  content="스타벅스는 세계에서 가장 큰 다국적 커피 전문점으로, 64개국에서 총 23,187개의 매점을 운영하고 있습니다."
/>
<meta property="twitter:image" content="./images/starbucks_seo.jpg" />
<meta property="twitter:url" content="https://starbucks.co.kr" />
```

# Google Fonts

- https://fonts.google.com/
- 라이센스 확인 필수

# Google Material Icons

- https://fonts.google.com/icons?selected=Material+Icons
- https://material.io/develop/web/getting-started
- 아이콘 기본 사이즈: 24px

# Header

- 크기와 상관없이(확대/축소) 가운데 정렬
  - 가로 지정 및 margin: 0 auto;

```css
header .inner {
  width: 1100px;
  margin: 0 auto;
}
```

- 이미지 태그 밑에 빈 공간
  1. 이미지 태그는 인라인 속성
  2. 인라인 속성은 baseline을 기준으로 약간의 공간을 가지는 구조
  3. display: block; 선언하여 공간 제거

```css
img {
  display: block;
}
```

- 수직 가운데 정렬
  - 요소의 높이 지정 필수

```css
.item {
  height: 75px;
  position: absolute;
  top: 0;
  bottom: 0;
  margin: auto;
}
```

- 수평 가운데 정렬
  - 요소의 너비 지정 필수

```css
.item {
  width: 75px;
  position: absolute;
  left: 0;
  right: 0;
  margin: auto;
}
```

### Sub Menu

---

- a태그 URL 임시처리 방법(href)
  1. \#
  1. javascript:void(0) : 권장

```html
<a href="javascript:void(0)">Sign In</a> <a href="#">Sign In</a>
```

- a태그 밑줄 제거

```css
a {
  text-decoration: none;
}
```

- li태그 사이에 구분선 표시
  1. 가상요소 사용(::before)
  1. content 속성 필수(content:"")
  1. 가상요소는 인라인 요소이기 때문에 가로 세로 값을 지정하기 위해 블록요소 설정(display:block;)
  1. position:absolute;를 선언한 경우 자동으로 block요소로 변경되기 때문에 display:block; 생략 가능

```css
header .sub-menu ul.menu li::before {
  content: '';
  width: 1px;
  height: 12px;
  background-color: #e5e5e5;
  position: absolute;
  top: 0;
  bottom: 0;
  margin: auto;
}
header .sub-menu ul.menu li:first-child:before {
  display: none;
}
```

### Main Menu

---

- 드롭다운 영역 설정
  1. position:fixed; 설정하여 viewport 기준으로 변경
  2. width: 100%; left:0; 너비 꽉차게 설정
  3. default로 숨김 처리 후 main menu hover일 경우 화면 노출

```css
header .main-menu .item .item__contents {
  width: 100%;
  position: fixed;
  left: 0;
  display: none;
}
header .main-menu .item:hover .item__contents {
  display: block;
}
```

### BEM(Block Element Modifier) : CSS 방법론

---

- 요소\_\_일부분: Underscore(Lodash) 기호로 요소의 일부분을 표시

```html
<div class="container">
  <div class="container__name"></div>
  <div class="item">
    <div class="item_name"></div>
  </div>
</div>
```

- 요소--상태: Hyphen(Dash) 기호로 요소의 상태를 표시

```html
<div class="btn btn--primary"></div>
<div class="btn btn--success"></div>
<div class="btn btn--error"></div>
```

### 전역배지

---

1. 모서리 둥글게 border-radius 설정 후 overflow:hidden; 설정 필수
2. 그림자 효과 box-shadow: offset-x, offset-y, blur-radius, spread-radius

- offset-x, offset-y: 그림자의 위치 설정
- blur-radius: 그림자 테두리(양수 값이 커질 수록 테두리가 흐려짐)
- spread-radius: 그림자 확산(양수 값이 커질 수록 그림자가 확산)

```css
header .badges .badge {
  border-radius: 10px;
  overflow: hidden;
  margin-bottom: 12px;
  box-shadow: 4px 4px 10px rgb(0, 0, 0, 0.15);
  cursor: pointer;
}
```

- 일정범위 스크롤 시 뱃지 숨기기
  1. window scroll 이벤트 사용
  1. scroll listener의 부하를 줄이기 위해 lodash 라이브러리 사용
     - lodash cdn 검색
  1. \_.throttle 함수 사용
     - \_.throttle(함수, 시간)
  1. gsap animation 라이브러리 사용
     - gsap cdn 검색
     - gsap.to(요소, 지속시간, 옵션)
     - opacity: 0은 시각적으로만 사라지기 때문에 display:'none'도 추가
       - 시각적으로만 사라질 경우 링크 이동의 버그 발생

```js
const badgeEl = document.querySelector('header .badges');

window.addEventListener(
  'scroll',
  _.throttle(function () {
    if (window.scrollY > 500) {
      gsap.to(badgeEl, 0.6, {
        opacity: 0,
        display: 'none',
      });
    } else {
      gsap.to(badgeEl, 0.6, {
        opacity: 1,
        display: 'block',
      });
    }
  }, 300)
);
```

### position: absolute; 배치기준

---

- position: absolute; 선언 시, 부모 요소를 기준으로 배치
- 구조적 부모 요소에 position이 선언 되어있는지 확인(position:static;은 제외)

### 순차적 애니메이션

---

1. fade-in 클래스 요소 전체를 가져온 후 반복문을 통해 순차적으로 요소 확인
1. gsap 애니메이션 라이브러리 사용
1. gsap의 delay 옵션 사용
1. 순차적으로 보여주기 위해 index 매개변수 사용

```javascript
const fadeEls = document.querySelectorAll('.fade-in');

fadeEls.forEach(function (fadeEl, index) {
  gsap.to(fadeEl, 1, {
    delay: (index + 1) * 0.7,
    opacity: 1,
  });
});
```

### 공지사항

---

- 공지사항 수직 슬라이드
  - swiperjs 사용
  - 예시) https://codesandbox.io/s/ngoi8?file=/index.html:1404-1877

```html
<link rel="stylesheet" href="https://unpkg.com/swiper/swiper-bundle.min.css" />
<script src="https://unpkg.com/swiper/swiper-bundle.min.js"></script>
```

```javascript
//new Swiper(선택자, 옵션)
new Swiper('.notice-line .swiper-container', {
  direction: 'vertical',
  autoplay: true,
  loop: true,
});
```

- 프로모션
  1. 확대/축소 시 항상 가운데 배치
     - 이미지 3개 가로(819px) + 이미지 사이 간격 2개(10px)를 프로모션 가로 영역으로 계산
     - position absoulte 속성으로 좌측에서 50%에 위치
     - 가로 전체 영역의 절반만큼 margin-left 감소

```css
.notice .promotion {
  height: 693px;
  background-color: #f6f5ef;
  position: relative;
}
.notice .promotion .swiper-container {
  width: calc(819px * 3 + 20px);
  height: 553px;
  position: absolute;
  top: 40px;
  left: 50%;
  margin-left: calc((819px * 3 + 20px) / -2);
}
```

2. 프로모션 수평 슬라이드
   - 3개씩 5초 간격으로 자동 슬라이드
   - 활성화된 프로모션만 잘 보이도록(.swiper-slide-active 클래스 이용)
   - 이전/다음 버튼 및 페이징 표시

```html
<div class="swiper-pagination"></div>
<div class="swiper-prev">
  <div class="material-icons">arrow_back</div>
</div>
<div class="swiper-next">
  <div class="material-icons">arrow_forward</div>
</div>
```

```css
.notice .promotion .swiper-slide {
  opacity: 0.5;
  transition: opacity 1s;
  position: relative;
}
.notice .promotion .swiper-slide-active {
  opacity: 1;
}
.notice .promotion .swiper-pagination .swiper-pagination-bullet {
  background-image: url('../images/promotion_slide_pager.png');
  background-color: transparent;
  width: 12px;
  height: 12px;
  margin-right: 6px;
  outline: none;
}
.notice .promotion .swiper-pagination .swiper-pagination-bullet:last-child {
  margin-right: 0;
}
.notice .promotion .swiper-pagination .swiper-pagination-bullet-active {
  background-image: url('../images/promotion_slide_pager_on.png');
}
.notice .promotion .swiper-prev,
.notice .promotion .swiper-next {
  width: 42px;
  height: 42px;
  border: 2px solid #333;
  border-radius: 50%;
  position: absolute;
  top: 300px;
  z-index: 1;
  cursor: pointer;
  outline: none;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: 0.4s;
}
.notice .promotion .swiper-prev {
  left: 50%;
  margin-left: -480px;
}
.notice .promotion .swiper-next {
  right: 50%;
  margin-right: -480px;
}
.notice .promotion .swiper-prev:hover,
.notice .promotion .swiper-next:hover {
  background-color: #333;
  color: #fff;
}
```

```javascript
new Swiper('.promotion .swiper-container', {
  slidesPerView: 3, //한번에 보여줄 슬라이드 개수
  spaceBetween: 10, //슬라이드 사이 여백
  centeredSlides: true, //1번 슬라이드가 가운데 보이기
  autoplay: {
    delay: 5000,
  },
  loop: true,
  pagination: {
    el: '.promotion .swiper-pagination', //페이지 번호 요소 선택자
    clickable: true,
  },
  navigation: {
    prevEl: '.promotion .swiper-prev',
    nextEl: '.promotion .swiper-next',
  },
});
```

### Youtube iframe API

---

1. 16:9 비율
   - height 설정 없이 padding-top 값은 부모의 가로 비율로 높이 지정
   - padding-top: 56.25%;는 가로:세로 비율 16:9

```html
<section class="youtube">
  <div class="youtube__area">
    <div id="player"></div>
  </div>
  <div class="youtube__cover"></div>
</section>
```

```css
.youtube .youtube__area {
  width: 1920px;
}
.youtube .youtube__area::before {
  content: '';
  display: block;
  width: 100%;
  height: 0;
  padding-top: 56.25%;
}
```

2. Youtube API
   - youtube iframe api 검색
   - youtube.js 참고
   - onYouTubeIframeAPIReady 함수명 변경하면 안됨

### Parallax Scrolling

---

- 백그라운드 이미지를 고정하여 스크롤 시, 백그라운드 이미지 안의 이미지와 Parallax Scrolling 효과 구현
- background-attachment: fixed; 이용
  - viewport 기준으로 이미지 고정

```html
<section class="pick-your-favorite">
  <div class="inner">
    <div class="text-group">
      <img src="./images/favorite_text1.png" alt="" class="title" />
      <img src="./images/favorite_text2.png" alt="" class="description" />
      <div class="more">
        <a href="javascript:void(0)" class="btn btn--white">자세히 보기</a>
      </div>
    </div>
  </div>
</section>
```

```css
.pick-your-favorite {
  background-image: url('../images/favorite_bg.jpg');
  background-repeat: no-repeat;
  background-position: center;
  background-attachment: fixed;
  background-size: cover;
}
.pick-your-favorite .inner {
  padding: 110px 0;
}
.pick-your-favorte .text-group {
  margin-left: 100px;
  display: flex;
  width: 362px;
  flex-wrap: wrap;
  justify-content: flex-end;
}
```

### 3D 애니메이션

---

- 개념
  1. 두개의 이미지 요소를 합친다.(position:absolute;)
  1. 하나의 이미지를 180도 돌린다.(trasnform:rotateY(-180deg);)
  1. 뒷면이 보이지 않도록 설정한다.(backface-visibility:hidden;)
  1. 해당 이미지 hover 시, 180도 돌려준다.
  1. 자연스러운 효과를 주기 위해 transition 속성을 부여한다.
  1. 3D 효과를 주기 위해 부모 요소에 perspective 속성을 부여한다.

```html
<section class="reserve-store">
  <div class="inner">
    <div class="medal">
      <div class="front">
        <img src="./images/reserve_store_medal_front.png" alt="" />
      </div>
      <div class="back">
        <img src="./images/reserve_store_medal_back.png" alt="" />
      </div>
    </div>
  </div>
</section>
```

```css
.reserve-store .inner {
  height: 600px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.reserve-store .medal {
  width: 334px;
  height: 334px;
  perspective: 600px;
}
.reserve-store .medal .front,
.reserve-store .medal .back {
  width: 334px;
  height: 334px;
  backface-visibility: hidden;
  transition: 1s;
}
.reserve-store .medal .front {
  position: absolute;
  transform: rotateY(0deg);
}
.reserve-store .medal:hover .front {
  transform: rotateY(180deg);
}
.reserve-store .medal .back {
  transform: rotateY(-180deg);
}
.reserve-store .medal:hover .back {
  transform: rotateY(0deg);
}
```

### ScrollMagic Library

---

- scrollMagic cdn 검색
- https://github.com/janpaepke/ScrollMagic

### Footer

---

- `&copy;` &copy;
- `&lt;` &lt;
- `&gt;` &gt;
- html entities 검색
  - https://dev.w3.org/html5/html-author/charref
- img 요소가 display:block; + margin:0 auto;인 경우  
  width 속성이 없어도 가운데 정렬 가능

### 페이지 상단으로 이동 버튼

---

- gsap scrollToPlugin 사용

<br/>
<br/>
<br/>

# 정리

## 1. html head

---

- favicon
  - favicon.ico는 index.html와 동일 위치이면 자동으로 설정
  - favicon.png파일로 설정하고 싶은 경우 link 태그로 명시
- Open Graph
  - 소셜 미디어로 공유할 때 사용되는 정보
- Reset CSS
  - https://www.jsdelivr.com/package/npm/reset-css 접속하여 reset.min.css 복사 및 적용
- Google Fonts
  - https://fonts.google.com/
  - 원하는 폰트 검색 및 선택
  - 실제 사용할 폰트 굵기만 선택. 너무 많이 선택 시 용량이 커짐
  - link 태그 복사해서 추가 및 css에 font-family 속성 적용
- Google Material Icons
  - https://material.io/develop/web/getting-started
  - 위 사이트에서 link 태그 복사해서 적용
  - https://fonts.google.com/icons?selected=Material+Icons
  - 위 사이트에서 원하는 아이콘 검색
  - 아이콘 적용은 .material-icons 클래스(div/span 태그)안에 해당 아이콘명 입력
  - 아이콘 기본 사이즈는 24px

<br/>
<br/>

## 2. Header

---

- ### **`유용한 CSS`**

  1. **가운데 정렬(확대/축소해도 가운데 배치)**
     - 가로(width) 선언 및 margin:0 auto;
  2. **수직 center 정렬**
     - positon: absolute; top:0; bottom:0; margin: auto; height: 90px;
     - 브라우저가 가운데를 맞추기 위해 `높이(height) 선언 필수`
  3. **수평 center 정렬은 수직과 반대**
     - top -> left / bottom -> right / height -> width

<br/>
<br/>

- ### 서브메뉴 돋보기(검색) 버튼 원리

  ***

  #### **`원리`**

  1.  기본은 돋보기(검색) 버튼
  1.  버튼 클릭 시, input이 늘어나고 돋보기(검색) 버튼 사라짐
  1.  input focus가 사라질 때 원상태로 복귀

  ***

  #### **`구현`**

  1.  **javascript에서 검색 버튼과 input element에 접근하여 검색버튼 클릭 시, input을 focus 하는 이벤트리스너 추가**

  ```javascript
  const searchEl = document.querySelector('.search');
  const searchInputEl = searchEl.querySelector('input');

  searchEl.addEventListener('click', function () {
    searchInputEl.focus();
  });
  ```

  2.  **input foucs 시, 클래스를 추가하여 input 요소 스타일 변경. 버튼 아이콘은 숨김 처리**

  ```javascript
  searchInputEl.addEventListener('focus', function () {
    searchEl.classList.add('focused');
    searchInputEl.setAttribute('placeholder', '통합검색');
  });
  ```

  ```css
  header .sub-menu .search input:focus {
    width: 190px;
    border-color: #669900;
  }
  header .sub-menu .search.focused .material-icons {
    opacity: 0;
  }
  ```

  3.  **input blur 이벤트에서 추가했던 클래스를 제거하여 원상태로 복귀**

  ```javascript
  searchInputEl.addEventListener('blur', function () {
    searchEl.classList.remove('focused');
    searchInputEl.setAttribute('placeholder', '');
  });
  ```

<br/>
<br/>

- ### 태그 사이에 구분선 추가

---

#### **`원리`**

1. 가상요소 사용(::before)
1. 가상요소는 `content 속성` 필수
1. 가상요소는 `인라인 요소`이기 때문에 가로,세로, 위아래 여백을 주기 위해 `블럭 속성` 필요
1. position:absoulte; 선언 시, 인라인 요소는 자동으로 블럭 요소로 변경됨

#### **`구현`**

1. li 태그 사이에 가상요소로 1px의 선을 추가
1. 첫번째 자식 요소는 숨김처리

```ccc
header .sub-menu ul.menu li::before {
  content: '';
  width: 1px;
  height: 12px;
  background-color: #e5e5e5;
  position: absolute;
  top: 0;
  bottom: 0;
  margin: auto;
}
header .sub-menu ul.menu li:first-child:before {
  display: none;
}
```

<br/>
<br/>

- ### 드롭다운 메뉴

---

#### **`원리`**

1. 메뉴명과 메뉴 내용 두개의 영역으로 나눈다.
1. 메뉴 내용 부분은 숨겨놓고 메뉴명에 마우스가 올라갈 때 보여준다.
1. (★중요) 메뉴 내용은 부모 요소가 아닌 브라우저 기준으로 꽉 채워서 보여주기 위해  
   width:100%; position: fixed; left: 0; 속성을 사용한다. (viewport 기준)
   - position: absolute;를 사용하면 부묘 요소를 기준으로 하기 때문에 좌우 끝까지 늘어날 수 없다.
   - top, bottom 속성을 사용하지 않아 수직 위치 값이 없으면 요소의 원래 위치를 그대로 사용한다.

#### **`구현`**

1. **메뉴명 스타일 구현**

```css
header .main-menu {
  display: flex;
  position: absolute;
  bottom: 0;
  right: 0;
  z-index: 1;
}
header .main-menu .item .item__name {
  padding: 10px 20px 34px 20px;
  font-family: Arial, sans-serif;
  font-size: 13px;
}
header .main-menu .item:hover .item__name {
  background-color: #2c2a29;
  color: #669900;
  border-radius: 6px 6px 0 0;
}
```

2. **메뉴 내용 스타일 구현(default는 숨김처리)**

```css
header .main-menu .item .item__contents {
  width: 100%;
  position: fixed;
  left: 0;
  display: none;
}
```

3. **메뉴에 마우스 hover 시 메뉴 내용 노출**

```css
header .main-menu .item:hover .item__contents {
  display: block;
}
```

<br/>
<br/>

- ### GSAP Library

---

    - javascript Animation Library
    - https://cdnjs.com/libraries/gsap

#### **`사용법`**

```javascript
gsap.to(요소, 시간, 옵션);

const badgeEl = document.querySelector('header .badges');

//뱃지 Element가 0.6초 동안 사라진다
gsap.to(badgeEl, 0.6, {
  opacity: 0,
  display: 'none',
});

const fadeEls = document.querySelectorAll('.fade-in');

//순차적으로 보여줄 요소들을 0.7초 간격으로 보여준다
fadeEls.forEach(function (fadeEl, index) {
  gsap.to(fadeEl, 1, {
    delay: (index + 1) * 0.7,
    opacity: 1,
  });
});
```

<br/>
<br/>

- ### Swiper API

---

    - Touch Slider
    - https://swiperjs.com/

#### **`사용법`**

```html
<link rel="stylesheet" href="https://unpkg.com/swiper/swiper-bundle.min.css" />
<script src="https://unpkg.com/swiper/swiper-bundle.min.js"></script>
```

```javascript
//new Swiper(선택자, 옵션)
new Swiper('.notice-line .swiper-container', {
  direction: 'vertical', //slide 방향(default:'horizontal')
  autoplay: true, //자동재생 여부
  loop: true, //반복여부
  slidesPerView: 3, //한번에 보여줄 슬라이드 개수
  spaceBetween: 10, //슬라이드 사이 여백
  centeredSlides: true, //1번 슬라이드가 가운데 보이기
  pagination: {
    el: '.promotion .swiper-pagination', //페이지 번호 요소 선택자
    clickable: true,
  },
  navigation: {
    prevEl: '.promotion .swiper-prev', //이전버튼 요소
    nextEl: '.promotion .swiper-next', //다음버튼 요소
  },
  //  autoplay: {
  //   delay: 5000, //autoplay 옵션
  // }
});
```

<br/>
<br/>

- ### Youtube API

---

    - 가로:세로 비율

      - height 설정 없이 padding-top을 부모의 가로 비율로 높이 지정
      - ex) width: 1920px; 이고 padding-top:56.25%인 경우 가로:세로 비율은 16:9
     heigth = 1920 \* 9 / 16

    - https://developers.google.com/youtube/iframe_api_reference?hl=ko#Requirements

#### **`사용법`**

1. Youtube API 코드가 다운로드 되는 즉시 `onYouTubeIframeAPIReady` 함수를 실행하기 때문에 함수명을 변경하면 안된다.

```html
<script defer src="./js/youtube.js"></script>
<div id="player"></div>
```

```javascript
youtube.js;

var tag = document.createElement('script');
tag.src = 'https://www.youtube.com/iframe_api';
var firstScriptTag = document.getElementsByTagName('script')[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

function onYouTubeIframeAPIReady() {
  new YT.Player('player', {
    videoId: 'An6LvWQuj_8', //최초 재생할 유튜브 영상 ID
    playerVars: {
      autoplay: true, //자동재생 유무
      loop: true, //반복재생 유무
      playlist: 'An6LvWQuj_8', //반복 재생할 유튜브 영상 ID 목록
    },
    events: {
      onReady: function (event) {
        event.target.mute(); //음소거
      },
    },
  });
}
```

<br/>
<br/>

- ### Parallax Scrolling

---

    - 배경과 컨텐츠의 움직임에 차이를 두어 평면에 공간적 깊이를 더해주는 시각적 효과

#### **`원리`**

1. 부모 요소의 백그라운드 이미지를 viewport 기준으로 고정시키고(fixed) 이미지를 제일 크게 설정(cover)
1. 스크롤 시, 부모 요소는 고정되어 자식 요소만 움직이는 시각적 효과를 보여줌

#### **`구현`**

```css
.pick-your-favorite {
  background-image: url('../images/favorite_bg.jpg');
  background-repeat: no-repeat;
  background-position: center;
  background-attachment: fixed;
  background-size: cover;
}
```

# 결론

- CSS는 어렵다
