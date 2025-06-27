<template>
    <section class="briefs-container container" id="briefsSection">
        <div class="wrapper-content-top">
            <div class="container">
                <div class="head-container col-start-1 col-end-5 tb:col-start-2 tb:col-end-6 dk:col-start-2 dk:col-end-5">
                    <h2 class="briefs-title" ref="briefsTitleRef">Les derniers briefs</h2>
                    <div ref="briefsLinkRef"> 
                        <nuxt-link to="/archives" class="briefs-link disabled">
                            <span>voir tout</span>
                            <svg width="6" height="6" viewBox="0 0 6 6" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path fill-rule="evenodd" clip-rule="evenodd" d="M0.706523 0.654888C0.586107 0.775299 0.586107 0.970523 0.706523 1.09093L4.80517 5.18958H2.15788C1.98759 5.18958 1.84955 5.32766 1.84955 5.49792C1.84955 5.66818 1.98759 5.80625 2.15788 5.80625H5.54955C5.63132 5.80625 5.70976 5.77375 5.7676 5.71597C5.82538 5.65813 5.85788 5.57969 5.85788 5.49792V2.10624C5.85788 1.93596 5.71981 1.79791 5.54955 1.79791C5.37928 1.79791 5.24121 1.93596 5.24121 2.10624V4.75354L1.14257 0.654882C1.02216 0.534472 0.826934 0.534472 0.706523 0.654888Z" fill="white"/>
                            </svg>
                        </nuxt-link>
                    </div>
                </div>
            </div>
        </div>
        <div class="margin-top-40">
            <div class="container-3" ref="container3Ref">
                <div class="brief-title col-start-1 col-end-2 tb:col-start-2 tb:col-end-3 dk:col-start-2 dk:col-end-3">PROJECT NAME</div>
                <div class="brief-title col-start-2 col-end-3 tb:col-start-3 tb:col-end-4 dk:col-start-3 dk:col-end-4">NB ÉQUIPE</div>
                <div class="brief-title col-start-3 col-end-4 tb:col-start-5 tb:col-end-6 dk:col-start-4 dk:col-end-5 flex-end">DATE RENDU</div>
                <div class="line-bottom col-start-1 col-end-4 tb:col-start-2 tb:col-end-6 dk:col-start-2 dk:col-end-5"></div>
            </div>
            <div class="container-3" v-for="item in items" :key="item.title" ref="container3ItemRef">
                <div class="brief-title-item col-start-1 col-end-2 tb:col-start-2 tb:col-end-3 dk:col-start-2 dk:col-end-3">{{ item.title }}</div>
                <div class="brief-description-item col-start-2 col-end-3 tb:col-start-3 tb:col-end-4 dk:col-start-3 dk:col-end-4">{{ item.nbEquipe }}</div>
                <div class="brief-description-item col-start-3 col-end-4 tb:col-start-5 tb:col-end-6 dk:col-start-4 dk:col-end-5 flex-end">{{ item.dateRendu }}</div>
                <div class="line-bottom col-start-1 col-end-4 tb:col-start-2 tb:col-end-6 dk:col-start-2 dk:col-end-5"></div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { LOADER_PLAYED } from '@/utils/constant';
import gsap from 'gsap';

const briefsTitleRef = ref(null);
const briefsLinkRef = ref(null);
const container3Ref = ref(null);
const container3ItemRef = ref([]);

const items = [
    {
        title: 'ECHECH AU ROI',
        nbEquipe: '7 ÉQUIPES',
        dateRendu: '25/05/25'
    },
    {
        title: 'ECHECH AU ROI',
        nbEquipe: '7 ÉQUIPES',
        dateRendu: '25/05/25'
    },
    {
        title: 'ECHECH AU ROI',
        nbEquipe: '7 ÉQUIPES',
        dateRendu: '25/05/25'
    },
    {
        title: 'ECHECH AU ROI',
        nbEquipe: '7 ÉQUIPES',
        dateRendu: '25/05/25'
    },
    {
        title: 'ECHECH AU ROI',
        nbEquipe: '7 ÉQUIPES',
        dateRendu: '25/05/25'
    },
    {
        title: 'ECHECH AU ROI',
        nbEquipe: '7 ÉQUIPES',
        dateRendu: '25/05/25'
    },
    {
        title: 'ECHECH AU ROI',
        nbEquipe: '7 ÉQUIPES',
        dateRendu: '25/05/25'
    }
]

const route = useRoute();

onMounted(() => {
    const delay = LOADER_PLAYED.PLAYED == 'true' || route.path !== '/' ? 0 : 4.5;

    const tl = gsap.timeline({delay: delay});

    tl.fromTo(briefsTitleRef.value, {
        y: 100,
    }, {
        y: 0,
        duration: 1.2,
        ease: 'power2.out',
    })

    tl.fromTo(briefsTitleRef.value, {
        opacity: 0,
    }, {
        opacity: 1,
        duration: 0.6,
        ease: 'linear',
    }, "<")

    tl.fromTo(briefsLinkRef.value, {
        opacity: 0,
    }, {
        opacity: 1,
        duration: 0.7,
        ease: 'linear',
    },"<+0.4")

    tl.fromTo([container3Ref.value, ...container3ItemRef.value], {
        y: 100,
    }, {
        y: 0,
        duration: 1.2,
        stagger: 0.1,
        ease: 'power2.out',
    },"<+0.1")

    tl.fromTo([container3Ref.value, ...container3ItemRef.value], {
        opacity: 0,
    }, {
        opacity: 1,
        stagger: 0.1,
        duration: 0.6,
        ease: 'linear',
    }, "<")

});	

</script>

<style scoped lang="scss">
.briefs-container{
    padding: 8rem;
    grid-template-rows: repeat(4, minmax(0, 1fr));
    height: 100vh;

    .margin-top-40{
        margin-top: 40px;
    }

    .wrapper-content-top{
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
    }

    .head-container{
        display: flex;
        justify-content: space-between;
        align-items: flex-end;

        .briefs-title{
            @include instrumentserif(400);
            font-size: 28rem;
            color: $white;

            @include tablet{
                font-size: 56rem;
            }
        }
        .briefs-link{
            display: block;
            @include ppneuemontreal(800);
            font-size: 7rem;
            color: $white;
            text-transform: uppercase;
            white-space: nowrap;
            margin-bottom: 6rem;
            
            @include tablet{
                font-size: 10rem;
            }

            svg{
                width: 6rem;
                height: 6rem;
                margin-left: 8rem;
            }
        }
    }

    .brief-title{
        @include ppneuemontreal(700);
        font-size: 7rem;
        color: $white;
        text-transform: uppercase;
        opacity: 0.3;

        @include tablet{
            font-size: 10rem;
        }
    }

    .brief-title-item{
        @include ppneuemontreal(700);
        font-size: 8rem;
        color: $white;
        text-transform: uppercase;

        @include tablet{
            font-size: 12rem;
        }
    }

    .brief-description-item{
        @include ppneuemontreal(500);
        font-size: 8rem;
        color: $white;
        text-transform: uppercase;
        opacity: 0.5;

        @include tablet{
            font-size: 12rem;
        }
    }

    .flex-end{
        display: flex;
        justify-content: flex-end;
    }

    .line-bottom{
        width: 100%;
        height: 0.5px;
        background-color: $white;
        opacity: 0.4;
        margin: 16px 0;
    }

}
</style>