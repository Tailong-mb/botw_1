<template>
    <section class="briefs-container container" id="creditsSection">
        <div class="wrapper-content-top">   
            <div class="container">
                <div class="head-container col-start-1 col-end-5 tb:col-start-2 tb:col-end-6 dk:col-start-2 dk:col-end-5">
                    <h2 class="briefs-title" ref="creditsTitleRef">Credits</h2>
                </div>
            </div>
        </div>
        <div class="margin-top-40">
            <div class="container" ref="container3Ref">
                <div class="brief-title col-start-1 col-end-2 tb:col-start-2 tb:col-end-3 dk:col-start-2 dk:col-end-3">NAME</div>
                <div class="brief-title col-start-2 col-end-3 tb:col-start-5 tb:col-end-6 dk:col-start-4 dk:col-end-5 flex-end">RÔLE</div>
                <div class="line-bottom col-start-1 col-end-3 tb:col-start-2 tb:col-end-6 dk:col-start-2 dk:col-end-5"></div>
            </div>
            <div class="container" v-for="item in items" :key="item.title" ref="container3ItemRef">
                <div class="brief-title-item col-start-1 col-end-2 tb:col-start-2 tb:col-end-3 dk:col-start-2 dk:col-end-3">{{ item.name }}</div>
                <div class="brief-description-item col-start-2 col-end-3 tb:col-start-5 tb:col-end-6 dk:col-start-4 dk:col-end-5 flex-end">{{ item.role }}</div>
                <div class="line-bottom col-start-1 col-end-3 tb:col-start-2 tb:col-end-6 dk:col-start-2 dk:col-end-5"></div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { LOADER_PLAYED } from '@/utils/constant';
import gsap from 'gsap';

const creditsTitleRef = ref(null);
const container3Ref = ref(null);
const container3ItemRef = ref([]);

const items = [
    {
        name: 'LESTY / PIERRE',
        role: 'FRONT-END DEVELOPER'
    },
    {
        name: 'MELTOZ / MAXIME',
        role: 'BACK-END DEVELOPER'
    },
    {
        name: 'Michael',
        role: 'FRONT-END DEVELOPER'
    },
    {
        name: 'PICHUNI / KIBO',
        role: 'BRIEF CREATOR'
    },
    {
        name: 'BESTEN / GUILLAUME',
        role: 'CONCEPT & ORGANIZER'
    },
    {
        name: 'KATY_V4 / CATHY DOLLE',
        role: 'CONCEPT & DESIGNER'
    },
]

const route = useRoute();

onMounted(() => {
    const delay = LOADER_PLAYED.PLAYED == 'true' || route.path !== '/' ? 0 : 4.5;

    const tl = gsap.timeline({delay: delay});

    tl.fromTo(creditsTitleRef.value, {
        y: 100,
    }, {
        y: 0,
        duration: 1.2,
        ease: 'power2.out',
    })

    tl.fromTo(creditsTitleRef.value, {
        opacity: 0,
    }, {
        opacity: 1,
        duration: 0.6,
        ease: 'linear',
    }, "<")

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
    height: 100vh;
    grid-template-rows: repeat(4, minmax(0, 1fr));

    .wrapper-content-top{
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
    }

    .margin-top-40{
        margin-top: 40px;
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
            @include ppneuemontreal(800);
            font-size: 7rem;
            color: $white;
            text-transform: uppercase;
            white-space: nowrap;

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
        white-space: nowrap;

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
        text-align: end;
        white-space: nowrap;
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