<template>
    <div class='loader' ref="loaderRef">
        <div class='relative-wrapper'>
            <div class='background container' ref="background">
                <div class="col-start-1 col-end-2">
                    <MarqueeLoader :images="loaderImages" />
                </div>
                <div class="col-start-2 col-end-3">
                    <MarqueeLoader :images="loaderImagesBottom" type="bottom" />
                </div>
                <div class="tb:col-start-3 tb:col-end-4 hide-mobile">
                    <MarqueeLoader :images="loaderImages2" />
                </div>
                <div class="tb:col-start-4 tb:col-end-5 hide-mobile">
                    <MarqueeLoader :images="loaderImagesBottom2" type="bottom" />
                </div>
                <div class="tb:col-start-5 tb:col-end-6 hide-mobile">
                    <MarqueeLoader :images="loaderImages3" />
                </div>
                <div class="tb:col-start-6 tb:col-end-7 hide-mobile">
                    <MarqueeLoader :images="loaderImagesBottom3" type="bottom" />
                </div>
                <div class="dk:col-start-7 dk:col-end-8 hide-tablet">
                    <MarqueeLoader :images="loaderImages4" />
                </div>
                <div class="dk:col-start-8 dk:col-end-9 hide-tablet">
                    <MarqueeLoader :images="loaderImagesBottom4" type="bottom" />
                </div>

            </div>
            <img :src="logo" alt="logo" ref="logoRef">
            <div class="loader-wrapper">
                <h1 ref="title" class="loader-item">Brief of the week</h1>
                <p ref="subtitle" class="loader-item">Data here</p>
            </div>
        </div>
    </div>
</template>

<script setup>
import gsap from 'gsap';
import MarqueeLoader from './MarqueeLoader.vue'
import logo from '@/public/images/logo.png'
import image1 from '@/public/images/loader/image-1.png'
import image2 from '@/public/images/loader/image-2.png'
import image3 from '@/public/images/loader/image-3.png'
import image4 from '@/public/images/loader/image-4.png'
import image5 from '@/public/images/loader/image-5.png'
import image6 from '@/public/images/loader/image-6.png'
import image7 from '@/public/images/loader/image-7.png'
import image8 from '@/public/images/loader/image-8.png'
import image9 from '@/public/images/loader/image-9.png'
import image10 from '@/public/images/loader/image-10.png'
import image11 from '@/public/images/loader/image-11.png'
import image12 from '@/public/images/loader/image-12.png'
import image13 from '@/public/images/loader/image-13.png'
import image14 from '@/public/images/loader/image-14.png'
import image15 from '@/public/images/loader/image-15.png'
import image16 from '@/public/images/loader/image-16.png'
import image17 from '@/public/images/loader/image-17.png'
import image18 from '@/public/images/loader/image-18.png'
import image19 from '@/public/images/loader/image-19.png'
import image20 from '@/public/images/loader/image-20.png'
import image21 from '@/public/images/loader/image-21.png'
import image22 from '@/public/images/loader/image-22.png'
import image23 from '@/public/images/loader/image-23.png'
import image24 from '@/public/images/loader/image-24.png'
import image25 from '@/public/images/loader/image-25.png'
import image26 from '@/public/images/loader/image-26.png'
import image27 from '@/public/images/loader/image-27.png'
import image28 from '@/public/images/loader/image-28.png'
import image29 from '@/public/images/loader/image-29.png'
import image30 from '@/public/images/loader/image-30.png'
import image31 from '@/public/images/loader/image-31.png'
import image32 from '@/public/images/loader/image-32.png'
import { LOADER_PLAYED } from '@/utils/constant';

const loaderImages = [image1, image2, image3, image4]
const loaderImagesBottom = [image5, image6, image7, image8]
const loaderImages2 = [image9, image10, image11, image12]
const loaderImagesBottom2 = [image13, image14, image15, image16]
const loaderImages3 = [image17, image18, image19, image20]
const loaderImagesBottom3 = [image21, image22, image23, image24]
const loaderImages4 = [image25, image26, image27, image28]
const loaderImagesBottom4 = [image29, image30, image31, image32]

const background = ref(null);
const title = ref(null);
const subtitle = ref(null);
const logoRef = ref(null);
const loaderRef = ref(null);

const lenis = useNuxtApp().$lenis;
const route = useRoute();

onMounted(() => {
    if (route.path === '/' && LOADER_PLAYED.PLAYED != 'true') {
        playLoader();
    } else if (loaderRef.value) {
        loaderRef.value.style.display = 'none';
        const tl = gsap.timeline();

        tl.add(() => {
            LOADER_PLAYED.PLAYED = 'true';
        }, 0.2)
    }
});

const playLoader = () => {
    const tl = gsap.timeline();

    lenis.stop();

    tl.to(background.value.querySelectorAll('img'), {
        opacity: 1,
        duration: 0.8,
        ease: 'linear',
        stagger:{
            amount: 0.9,
            from: 'center',
            grid: "auto",
        }
    })

    tl.fromTo(logoRef.value, {
        y: 100,
    }, {
        opacity: 1,
        y: 0,
        duration: 1.2,
        ease: 'power2.out',
    })
    tl.to(logoRef.value, {
        opacity: 1,
        duration: 0.6,
        ease: 'linear',
    }, "<+=0.6")

    tl.to([title.value, subtitle.value], {
        opacity: 1,
        duration: 0.6,
        stagger: 0.1,
        ease: 'linear',
    }, "-=0.3")

    tl.to(loaderRef.value, {
        clipPath: 'inset(0 0 100% 0)',
        duration: 1,
        ease: 'immg.zoomOut',
    },"+=0.2")

    tl.add(() => {
        LOADER_PLAYED.PLAYED = 'true';
        lenis.start()
    })

}
</script>

<style lang="scss" scoped>
.loader{
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1000;

    .relative-wrapper{
        position: relative;
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;

        .background{
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: $black;

            &::before{
                content: '';
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                background-color: $black;
                opacity: 0.5;
                z-index: 1;
            }

            img{
                opacity: 0;
            }

            .hide-mobile{
                display: none;

                @include tablet{
                    display: flex;
                }
            }

            .hide-tablet{
                display: none;

                @include desktop{
                    display: flex;
                }
            }   
        }
        
        img{
            position: relative;
            width: 269rem;
            height: auto;
            z-index: 2;
            opacity: 0;

            @include tablet{
                width: 350rem;
            }
        }

        .loader-wrapper{
            position: relative;
            width: 269rem;
            display: flex;
            justify-content: space-between;
            z-index: 2;

            @include tablet{
                width: 350rem;
            }

            .loader-item{
                @include ppneuemontreal(700);
                font-size: 6rem;
                color: $white;
                text-transform: uppercase;
                opacity: 0;

                @include tablet{
                    font-size: 8rem;
                }
            }
        }
    }
}

</style>