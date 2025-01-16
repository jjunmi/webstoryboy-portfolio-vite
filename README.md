# 포트폴리오 사이트 만들기 프로젝트

1. [vite](https://github.com/webstoryboy/port2023-vite)를 이용하여 사이트를 제작합니다. 
2. [react.js](https://github.com/webstoryboy/port2023-react)를 이용하여 사이트를 제작합니다. 
3. [vue.js](https://github.com/webstoryboy/port2023-vue)를 이용하여 사이트를 제작합니다.
4. [next.js](https://github.com/webstoryboy/port2023-next)를 이용하여 사이트를 제작합니다.

## 사용 스택
- vite(https://ko.vitejs.dev/) 를 사용하여 사이트를 번들링하고 관리합니다.
- gsap(https://greensock.com/gsap) 를 이용하여 패럴랙스 효과를 줍니다.
- lenis(https://lenis.studiofreight.com/) 를 이용하여 스므스 효과를 구현합니다.
- netlify(https://www.netlify.com/) 를 통해 사이트를 배포합니다.
- git(https://github.com/) 을 사용하여 파일을 관리합니다.
- HTML, CSS 기반으로 웹사이트의 기본 레이아웃 설계하고, 웹 표준 및 웹 접근성을 준수하여 작업합니다. [ARIA(Accessible Rich Internet Applications)](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles)

## 프로젝트 실행
(프로젝트 세팅)[https://webstoryboy.co.kr/1924]
- vite를 설치합니다. `npm create vite@latest`
- gsap를 설치합니다. `npm install gsap`
- lenis를 설치합니다. `npm install @studio-freight/lenis`
- vite를 설치 후 환경 설정을 합니다. `vite.config.js`파일을 만들고 다음과 같이 작성합니다.
```html
    <link rel="icon" type="image/svg+xml" href="assets/img/favicon.svg" />
```
```bash
    npm create vite@latest
    npm install
    npm run dev

    npm install gsap
    npm install @studio-freight/lenis
```
```javascript
// vite.config.js
export default {
    root: "src",
    build: {
    outDir: "../public",
    },
};
```
```css
    backdrop-filter: blur(15px);
    text-transform: uppercase;
    filter: grayscale(0); /* 흑백 */
    filter: grayscale(100%);
    text-decoration: underline;
    text-underline-position: under;
```
### 구조
- (ARIA) [https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/alert_role]
- role="banner", role="main", role="contentinfo"
- role="heading" 제목
- role="button"
- aria-controls="primary-menu"
- aria-expanded="false"
- aria-hidden="true" (꾸밈용 태그 : 라인 div > span)

```html
    <div id="skip">
        <a href="#header">헤더 영역 바로가기</a>
        <a href="#intro">소개 영역 바로가기</a>
        <a href="#skill">스킬 영역 바로가기</a>
        <a href="#site">사이트 영역 바로가기</a>
        <a href="#port">포트폴리오영역 바로가기</a>
        <a href="#contact">연락처 영역 바로가기</a>
        <a href="#footer">푸터 영역 바로가기</a>
    </div>
    <header id="header" role="banner">
        <div class="header__inner">
        <div class="header__logo">
            <a href="#">portfolio<em>developer</em></a>
        </div>
        <nav class="header__nav" role="navigation" aria-label="메인 메뉴">
            <ul>
                <li><a href="#intro">intro</a></li>
                <li><a href="#skill">skill</a></li>
                <li><a href="#site">site</a></li>
                <li><a href="#port">portfolio</a></li>
                <li><a href="#contact">contact</a></li>
            </ul>
        </nav>
        <div class="header__nav__mobile" id="headerToggle" aria-controls="primary-menu" aria-expanded="false" 
 role="button" tabindex="0">
            <span></span>
        </div>
    </div>
</header>
    <main id="main" role="main">
        <section id="intro"></section>
        <section id="skill"></section>
        <section id="site"></section>
        <section id="port"></section>
        <section id="contact"></section>
    </main>
    <footer id="footer" role="contentinfo"></footer>
```
```css
/* css > setting > style.css */
@charset "UTF-8";
/* setting */
@import url(setting/fonts.css);
@import url(setting/vars.css);
@import url(setting/reset.css);
/* section */
@import url(section/header.css);
@import url(section/intro.css);
@import url(section/skill.css);
@import url(section/site.css);
@import url(section/port.css);
@import url(section/contact.css);
@import url(section/footer.css);
```
```css
/* css > setting > fonts.css */
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@100;200;300;400;500;600;700;800;900&display=swap");
@import url("https://websfont.github.io/nanumSquareNeo/nanumSquareNeo.css");
@import url("https://websfont.github.io/gmarket/gmarket.css");

.mont {font-family: "Montserrat";}
.nanum {font-family: "nanumSquareNeo";}
.gmarket {font-family: "gmarket";}
```
```css
/* css > setting > vars */
:root {
    --mainEng-font: "Montserrat";
    --mainKor-font: "nanumSquareNeo";
    --mainNum-font: "gmarket";
  
    --mainBg-color: #f3ede8;
    --subBg100: #cdc0b1;
    --subBg200: #afa395;
    --subBg300: #81887c;
    --subBg400: #afa7a2;
    --subBg500: #a6afa2;
  
    --white: #fff;
    --black: #000;
    --black100: #2b2b2b;
    --black200: #434343;
    --black300: #686868;
    --black400: #e0e0e0;
  
    /* 기본 폰트 설정 */
    font-family: var(--mainEng-font), var(--mainKor-font);
    font-size: 16px;
    line-height: 1.5;
    font-weight: 400;
  
    /* 폰트를 부드럽게 렌더링하기 위한 속성  */
    font-synthesis: none;
    text-rendering: optimizeLegibility;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  
    /* 아이폰 가로 모드에서 글씨 확대 금지 */
    -webkit-text-size-adjust: 100%;
}
@media (max-width: 800px) {
    :root {
        font-size: 14px;
        line-height: 1.4;
    }
}
body {color: var(--black100);background-color: var(--mainBg-color);}
```
```javascript
// js > menu.js
export function menu() {
    const headerToggle = document.getElementById("headerToggle");
    const headerNav = document.querySelector(".header__nav");

    if(headerToggle){
        headerToggle.addEventListener('click', () => {
            headerNav.classList.toggle("show");
            
            headerToggle.getAttribute("aria-expanded") === "true" 
            ? headerToggle.setAttribute("aria-expanded", "false") 
            : headerToggle.setAttribute("aria-expanded" , "true");
        });
    }
}
```
```javascript
//link.js
export function link() {
    document.querySelectorAll("a[href^='#']").forEach((anchor) => {
        anchor.addEventListener('click', function(e) {
            e.preventDefault();

            const targetId = this.getAttribute("href");
            const targetElement = document.querySelector(targetId);

            if(targetElement) {
                targetElement.scrollIntoView({behavior: "smooth"});
            }
        })
    });
}
```
```javascript
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";

export function port() {
    gsap.registerPlugin(ScrollTrigger);
    const horSection = gsap.utils.toArray(".port__item");
    
    gsap.to(horSection, {
        xPercent: -100 * (horSection.length -1),
        ease: "none",
        scrollTrigger: {
            trigger: "#port",
            start: "top top",
            end: "+=3000",
            pin: true,
            scrub: 1,
            markers: false,
            invalidateOnRefresh: true,
            anticipatePin: 1,
        }
    })
}
```
