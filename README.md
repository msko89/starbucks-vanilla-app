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
