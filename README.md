
# php include    
```html
    <?php include ('header.html')?> 
    <?php include ('footer.html')?> 
```  

# setting  
```html  
    <!DOCTYPE html>
    <!-- <html xmlns="http://www.w3.org/1999/xhtml" lang="ko" xml:lang="ko"></html> -->
    <html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta http-equiv="content-language" content="kr" />
        <meta http-equiv="imagetoobar" content="no" />
        <meta name="viewport" content="width=device-width,initial-scale=1.0, maximum-scale=1, user-scalable=no" />
        <meta name="format-detection" content="telephone=no, address=no, email=no" />
    <!-- 사이트 기본설정 영역 START -->
    <!-- 수정사항 : url 수정 -->
        <meta name="Robots" content="index, follow" />
        <!-- <link rel="canonical" href="" />  -->
        <!-- SEO -->
        <meta name="title" content="" />
        <meta name="subject" content="" />
        <meta name="author" content="" />
        <meta name="keywords" content="" />
        <meta name="description" content="" />
        <!-- Open Graph -->
        <meta property="og:type" content="website" />
        <meta property="og:site_name" content="" />
        <meta property="og:title" content="" />
        <meta property="og:url" content="" />
        <meta property="og:image" content="" />
        <meta property="og:description" content="" />

        <meta name="twitter:card" content="summary" />
        <meta name="twitter:site" content="" />
        <meta name="twitter:title" content="" />
        <meta name="twitter:image" content="" />
        <meta name="twitter:url" content="" />
        <meta name="twitter:description" content="" />
        
        <!-- Naver webmaster Tool & Google Search Concole-->
        <!-- <meta name="naver-site-verification" content="" /> -->
        <!-- <meta name="google-site-verification" content="" /> -->
    <!-- 사이트 기본 설정 영역 END -->
        <title></title>
        <link rel="shorcut icon" href="./favicon.ico" type="image/x-icon" />
        <link rel="stylesheet" href="./css/reset.css" />
        <link rel="stylesheet" href="./css/main.css" />

        <!-- swiperslider -->
        <link rel="stylesheet" href="./css/swiper-bundle.min.css" />
        <script src="./js/jquery-3.7.0.min.js"></script>
        <script src="./js/swiper.min.js"></script>
        <!-- script -->
        <script src="./js/common.js" type="text/javascript"></script>
    </head>
    <body>
        <dl class="skipnav">
            <dt class="screenout">Skip navigation</dt>
            <dd><a href="#container">Go to main Contents</a></dd>
        </dl>
        <!-- Header start-->
        <header id="header"></header>
        <!-- Header end-->
        <!-- Container start-->
        <div id="container"></div>
        <!-- Container end-->
        <!-- Footer start-->
        <footer id="footer"></footer>
        <!-- Footer end-->
    </body>
    </html>
```  
  
# Javascript
```javascript
window.addEventListener('load', function() {
    //document.body.classList.toggle('active);
    //document.body.classList.remove('active);
    //document.body.classList.contains('active);
    //document.body.classList.add('active);

    searchBtn.addEventListener('click', function(e){
        searchWrapEl.classList.toggle('searching');
        if(searchWrapEl.classList.contains('.searching')){
            setTimeout(function(){
            searchInput.focus();//not working
            }, 500);
        }else{
            searchInput.value = '';
        }
        e.stopPropagation();
    });
    searchInput.addEventListener('click', (e) => e.stopPropagation());

    for(let i = 0; i < depthListEl.length; i++){
      depthListEl[i].addEventListener('click', function(){
          this.classList.toggle('active');
      });
    }
    window.addEventListener('resize', function() {
      if(window.innerWidth > 1280){
        gnbEl.classList.remove('active');
        document.body.classList.remove('fixed');
      }
    });

     // 요소의 가시성 관찰
    const io = new IntersectionObserver(function(entries){
      entries.forEach(function(entry) {
        if(!entry.isIntersecting) {
          return;
        }
        entry.target.classList.add('show');
      });
    });
    const sectionEl = document.querySelectorAll('.sec-animate');
    sectionEl.forEach(function(el){
      io.observe(el);
    });
    // 요소의 가시성 관찰 End

    //forEach Start
    //male-grooming / tab bar
    const tabLists = document.querySelectorAll('.tab-link-wrap li');
    const tabInfo = document.querySelectorAll('.tab-info-wrap');
    tabLists.forEach((tab, idx) => {
      tab.addEventListener('click', function() {
        tabInfo.forEach((inner)=> {
          inner.classList.remove('active');
        })
        tabLists.forEach((item) => {
          item.classList.remove('active');
        })
        tabInfo[idx].classList.add('active');
        tabLists[idx].classList.add('active');
      });
    });
    //forEach End
 ``` 

# JQUERY   
```javascript
    $(document).ready(function() {
        /* main - slider */
        var mainSlider = new Swiper(".main-slider", {
            slidesPerView: 1,
            loop: true,
            speed: 1500,
            autoplay: {
                delay: 4000,
                disableOnInteraction: false,
                },
            pagination: {
                el: ".swiper-pagination",
                clickable: true,
            },
            navigation: {
                nextEl: ".swiper-button-next",
                prevEl: ".swiper-button-prev",
            },
            });
            $(".swiper-button-play").click(function(){
            $(this).toggleClass('active');
            if($(this).hasClass('active') === true){
                mainSlider.autoplay.stop();
            }else{
                mainSlider.autoplay.start();
            }
        });
        /* main - product */
        var productSlider = new Swiper(".product-slider", {
            slidesPerView: 3.3,
            spaceBetween: 20,
            centeredSlides: true,
            loop: true,
            speed: 700,
            autoplay: {
                delay: 3000,
                disableOnInteraction: false,
            },
            navigation: {
            nextEl: ".swiper-button-next",
            prevEl: ".swiper-button-prev",
            },
            breakpoints: {
            768: {
                slidesPerView: 1.3,
            },
            }
        });
    });
```