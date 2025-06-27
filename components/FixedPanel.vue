<template>
    <div class="fixed-panel container" ref="fixedPanelRef">
        <div class="fixed-panel-wrapper col-start-1 col-end-5 tb:col-end-7 dk:col-start-6 dk:col-end-9">
            <div class="image-container">
                <div class="wrapper" ref="imageWrapperRef">
                    <img :src="placeholder" alt="placeholder" ref="imageRef"/>
                </div>
            </div>
            <div class="content-container">
                <div class='status' ref="statusRef">
                    <span class="status-title">{{ state[0].title }}</span>
                    <span class="square" :class="state[0].color"></span>
                </div>
                <h2 class="title" ref="titleRef">
                    Couleur café
                </h2>
                <div class="header-item hide-mobile margin-top-20" ref="headerItemDateRef">
                    débute le
                </div>
                <div class="content-item hide-mobile" ref="contentItemDateRef">
                    31.05.25
                </div>
                <div class="cta-container margin-top-20">
                    <div class="item">
                        <div class="header-item" ref="headerItemDesignersRef">
                            designers
                        </div>
                        <div class="content-item" ref="contentItemDesignersRef">
                            8
                        </div>
                    </div>
                    <div class="item">
                        <div class="header-item" ref="headerItemDevelopersRef">
                            developers
                        </div>
                        <div class="content-item" ref="contentItemDevelopersRef">
                            8
                        </div>
                    </div>
                    <div class="cta-container" ref="ctaContainerRef">
                        <Cta text="Voir le brief" link="#" ref="ctaRef" />
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import placeholder from '@/public/images/placeholder.png';
import Cta from '@/components/Cta.vue';
import gsap from 'gsap';
import { LOADER_PLAYED } from '@/utils/constant';

const state = [
    {
        title: "inscription",
        color: "green",
    },
    {
        title: "EN COURS",
        color: "orange",
    },
    {
        title: "brief terminé",
        color: "red",
    }
]

const fixedPanelRef = ref(null);
const imageWrapperRef = ref(null);
const imageRef = ref(null);
const statusRef = ref(null);
const titleRef = ref(null);
const headerItemDateRef = ref(null);
const contentItemDateRef = ref(null);
const headerItemDesignersRef = ref(null);
const contentItemDesignersRef = ref(null);
const headerItemDevelopersRef = ref(null);
const contentItemDevelopersRef = ref(null);
const ctaContainerRef = ref(null);
const ctaRef = ref(null);

const route = useRoute();

onMounted(() => {
    const delay = LOADER_PLAYED.PLAYED == 'true' || route.path !== '/' ? 0 : 4.5;

    const tl = gsap.timeline({delay: delay});

    tl.fromTo(fixedPanelRef.value, {
        xPercent: 100,
    }, {
        xPercent: 0,
        duration: 1.4,
        ease: 'immg.zoomOut',
    })

    tl.fromTo(imageWrapperRef.value, { 
        yPercent: -100,
    }, {
        yPercent: 0,
        duration: 1,
        ease: 'immg.zoomOut',
    })
    tl.fromTo(imageRef.value, { 
        yPercent: 100,
    }, {
        yPercent: 0,
        duration: 1,
        ease: 'immg.zoomOut',
    },"<")

    tl.fromTo([statusRef.value , titleRef.value, headerItemDateRef.value, contentItemDateRef.value, headerItemDesignersRef.value, contentItemDesignersRef.value, headerItemDevelopersRef.value, contentItemDevelopersRef.value], {
        opacity: 0,
    }, {
        opacity: 1,
        duration: 0.7,
        ease: 'linear',
        stagger: 0.15,
    },"<+0.5")

    tl.fromTo(ctaContainerRef.value, {
        y: 100,
    }, {
        y: 0,
        duration: 1.2,
        ease: 'power2.out',
    },"-=0.9")

    tl.fromTo(ctaContainerRef.value, {
        opacity: 0,
    }, {
        opacity: 1,
        duration: 0.6,
        ease: 'linear',
    }, "<+0.6")
})
</script>

<style lang="scss" scoped>
.fixed-panel {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    pointer-events: none;
    z-index: 100;

    .fixed-panel-wrapper {
        position: relative;
        height: 100rem;
        background-color: $white;
        pointer-events: auto;
        display: flex;

        @include tablet {
            height: 250rem;
        }

        @include desktop{
            height: 100vh;
            flex-direction: column;
        }

        .image-container{
            position: relative;
            width: 28%;
            height: 100%;

            @include desktop{
                height: 50%;
                width: 100%;
            }

            .wrapper{
                overflow: hidden;
                height: 100%;
            }
            
            img {
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
        }

        .content-container{
            padding: 10rem;
            width: 72%;

            @include tablet{
                padding: 20px;
            }

            @include desktop{
                padding: 40px 35rem;
                width: 100%;
            }

            @include large{
                padding: 90px 70rem;
            }

            .status{
                font-size: 7rem;
                @include ppneuemontreal(700);
                text-transform: uppercase;
                display: flex;
                align-items: center;

                @include tablet{
                    font-size: 10rem;
                }

                .status-title{
                    opacity: 0.3;
                }

                .square{
                    width: 5rem;
                    height: 5rem;
                    border-radius: 50%;
                    margin-left: 5rem;
                    
                    &.red{
                        background-color: $red;
                    }

                    &.orange{
                        background-color: $orange;
                    }   

                    &.green{
                        background-color: $green;
                    }

                    @include tablet{
                        width: 7rem;
                        height: 7rem;
                        margin-left: 8rem;
                    }
                }
            }

            .title{
                font-size: 20rem;
                @include ppeditorialnew(200);
                margin-top: 7px;

                @include desktop{
                    font-size: 40rem;
                }
            }

            .header-item{
                font-size: 7rem;
                @include ppneuemontreal(700);
                text-transform: uppercase;
                opacity: 0.3;
                
                @include tablet{
                    font-size: 10rem;
                }

                @include mobile-only{
                    display: none;
                }
            }

            .content-item{
                font-size: 28rem;
                @include ppeditorialnew(200);
                margin-top: 8px;

                @include mobile-only{
                    display: none;
                }
            }   

            .margin-top-20{
                margin-top: 20px;

                @include desktop{
                    margin-top: 48px;
                }
            }

            .cta-container{
                display: flex;
                justify-content: flex-end;
                align-items: flex-end;

                @include tablet{
                    justify-content: space-between;
                }
            }
        }
    }
}
</style>