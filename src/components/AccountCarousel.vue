<template>
  <div class="account-carousel-stage">
    <div class="comp-dash-account-carousel swiper-container" ref="accountCarousel">
      <div class="swiper-wrapper" ref="carouselWrapper">
        <div 
            v-for="account, index in accounts" 
            class="swiper-slide"
            :class="`account-slide-${index}`"
            :key="account.name"
        >
            {{ account.name }}
        </div>
      </div>
      <div class="swiper-pagination"></div>
    </div>
  </div>
</template>

<script>
import Swiper, { Pagination } from 'swiper';
Swiper.use([Pagination]);

export default {
    name: 'AccountCarousel',
    data () {
        return {
            accountCarousel: null,
            carouselOptions: null,
            accounts: [
                {
                    name: 'Account 1'
                },
                {
                    name: 'Account 2'
                },
                {
                    name: 'Account 3'
                },
                {
                    name: 'Account 4'
                },
                {
                    name: 'Account 5'
                },
            ]
        }
    },
    methods: {
        buildCarouselOptions() {
            let carouselOptions = {
                pagination: {
                    el: '.swiper-pagination',
                    clickable: true,
                },
                spaceBetween: 10, // achieves the 15px gap between carousel slides as prescribed in final design
                grabCursor: true,
                slidesPerView: 1.25,
                centeredSlides: true,
                a11y: {
                    containerMessage: 'Your Accounts',
                    paginationBulletMessage: 'Go to Account {{index}}',
                    lastSlideMessage: 'This is the last Account in this list'
                },
            }

            this.carouselOptions = carouselOptions;
        },
        initCarousel() {
            this.accountCarousel = new Swiper(this.$refs.accountCarousel, this.carouselOptions);
        },
        getTranslate3d (el) {
            let values = el.style.transform.split(/\w+\(|\);?/);
            if (!values[1] || !values[1].length) {
                return [];
            }
            return values[1].split(/,\s?/g);
        }
    },
    mounted () {
        this.buildCarouselOptions()
    },
    watch: {
        carouselOptions: function () {
            this.initCarousel();
        }
    },
}
</script>

<style>
.account-carousel-stage {
    max-width: 430px;
    margin: 0 auto;
}

/** * Swiper 6.8.4 * Most modern mobile touch slider and framework with hardware accelerated transitions * https://swiperjs.com * * Copyright 2014-2021 Vladimir Kharlampidi * * Released under the MIT License * * Released on: August 23, 2021 */
:root {
    --swiper-theme-color: #006eb2;
}
.swiper-container {
    margin-left:auto;
    margin-right:auto;
    position:relative;
    overflow:hidden;
    list-style:none;
    padding:0;
    z-index:1
}

.swiper-wrapper {
    position: relative;
    width: 100%;
    height: 100%;
    z-index: 1;
    display: flex;
    transition-property: transform;
    box-sizing: content-box
}
.swiper-container-android .swiper-slide,.swiper-wrapper {
    transform: translate3d(0px,0,0)
}

.swiper-container-pointer-events {
    touch-action: pan-y
}

.swiper-slide {
    flex-shrink: 0;
    /* width: 100%;
    height: 100%; */
    position: relative;
    transition-property: transform
}

.swiper-slide-invisible-blank {
    visibility: hidden
}
.swiper-container-autoheight,.swiper-container-autoheight .swiper-slide {
    height: auto
}

.swiper-pagination {
    position: absolute;
    text-align: center;
    transition: .3s opacity;
    transform: translate3d(0,0,0);
    z-index: 10;
    width: 100%;
}

.swiper-pagination.swiper-pagination-hidden{
    opacity: 0;
}

.swiper-pagination-bullet {
    width: 12px;
    height: 12px;
    display: inline-block;
    border-radius: 50%;
    background-color: #ccc;
    opacity: 0.2;
}

button.swiper-pagination-bullet {
    border: none;
    margin: 0;
    padding: 0;
    box-shadow: none;
    -webkit-appearance: none;
    appearance: none;
}
.swiper-pagination-clickable .swiper-pagination-bullet {
    cursor: pointer;
}
.swiper-pagination-bullet:only-child {
    display: none!important;
}
.swiper-pagination-bullet-active{
    opacity: 1;
    background: var(--swiper-pagination-color,var(--swiper-theme-color));
}

.swiper-container-horizontal>.swiper-pagination-bullets .swiper-pagination-bullet{
    margin:0 4px
}

.swiper-container-horizontal>.swiper-pagination-bullets.swiper-pagination-bullets-dynamic{
    left:50%;
    transform:translateX(-50%);
    white-space:nowrap
}

.swiper-container-horizontal>.swiper-pagination-bullets.swiper-pagination-bullets-dynamic .swiper-pagination-bullet{
    transition:.2s transform,.2s left
}

.swiper-container-horizontal.swiper-container-rtl>.swiper-pagination-bullets-dynamic .swiper-pagination-bullet{
    transition:.2s transform,.2s right
}

.swiper-container-horizontal>.swiper-pagination-progressbar,.swiper-container-vertical>.swiper-pagination-progressbar.swiper-pagination-progressbar-opposite{
    width:100%;
    height:4px;
    left:0;
    top:0
}
.swiper-container-horizontal>.swiper-pagination-progressbar.swiper-pagination-progressbar-opposite,.swiper-container-vertical>.swiper-pagination-progressbar{
    width:4px;
    height:100%;
    left:0;
    top:0
}

.swiper-pagination-lock{
    display:none
}

.swiper-container {
    height: 240px;
    padding-top: 6px;
}

.swiper-slide {
    border: 1px solid #ccc;
    transition: all .2s;
    height: 166px;
    background-color: white;
    border-radius: 15px;
    box-shadow: 0px 2px 8px 0px rgba(0, 0, 0, 0.25);
    margin-top: 10px;
}
.swiper-slide-active {
    margin-top: 0;
    height: 196px;
    margin-top: 0;
}

/** PAGINATION */ 
.swiper-pagination-bullets {
  bottom: 6px;
}

.swiper-pagination-bullet {
  height: 12px;
  width: 12px;
  opacity: 0.7;
  margin: 0 0.5rem 0 0;
  transition: all 0.2s;
  background-color: #ccc;
}

.swiper-pagination-bullet-active {
  background-color: #006eb2;
  opacity: 1;
}

.swiper-pagination-bullet-active:hover {
  opacity: 1;
}

/** CAROUSEL ADJUSTMENTS */
.account-slide-2.swiper-slide-prev {
    margin-left: -9px;
}

.account-slide-3.swiper-slide-prev {
    margin-left: -15px;
}
</style>
