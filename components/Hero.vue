<template>
    <section class="hero container" id="heroSection">
        <div class="key-words-desktop tb:col-start-1 tb:col-end-3">
            <h2 class="hero-title" ref="heroTitleRef">OBJECTIFS</h2>
            <ul>
                <li class="hero-content" ref="heroContentOneRef">Entraide</li>
                <li class="hero-content" ref="heroContentTwoRef">Communication</li>
                <li class="hero-content" ref="heroContentThreeRef">Empowerement</li>
                <li class="hero-content" ref="heroContentFourRef">Création</li>
            </ul>
        </div>
        <div class="hero-content-container tb:col-start-4 tb:col-end-7 dk:col-start-3 dk:col-end-5">
            <h2 class="hero-title" ref="heroSecondTitleRef">CONCEPT</h2>
            <p ref="heroContentFiveRef">Le BRIEF OF THE WEEK a été créé pour encourager la collaboration entre designers et développeurs. Chaque semaine, un brief créatif vous permet de pratiquer, d’apprendre à mieux travailler ensemble et de créer des projets.  Que vous débutiez ou soyez déjà expert, c’est l’occasion d’enrichir votre portfolio, de progresser, et de développer vos compétences en équipe.</p>
        </div>
        <div class="key-words-mobile">
            <h2 class="hero-title" ref="heroThirdTitleRef">OBJECTIFS</h2>
            <ul>
                <li class="hero-content" ref="heroContentSixRef">Entraide</li>
                <li class="hero-content" ref="heroContentSevenRef">Communication</li>
                <li class="hero-content" ref="heroContentEightRef">Empowerement</li>
                <li class="hero-content" ref="heroContentNineRef">Création</li>
            </ul>
        </div>
    </section>
</template>

<script setup>
import gsap from 'gsap';
import { LOADER_PLAYED } from '@/utils/constant';

const heroTitleRef = ref(null);
const heroSecondTitleRef = ref(null);
const heroThirdTitleRef = ref(null);
const heroContentOneRef = ref(null);
const heroContentTwoRef = ref(null);
const heroContentThreeRef = ref(null);
const heroContentFourRef = ref(null);
const heroContentFiveRef = ref(null);
const heroContentSixRef = ref(null);
const heroContentSevenRef = ref(null);
const heroContentEightRef = ref(null);
const heroContentNineRef = ref(null);

onMounted(() => {
    const delay = LOADER_PLAYED.PLAYED == 'true' ? 0 : 4.5;

    const tl = gsap.timeline({delay: delay});

    tl.fromTo([heroTitleRef.value, heroSecondTitleRef.value, heroThirdTitleRef.value], {
        y: 100,
    }, {
        y: 0,
        duration: 1.2,
        ease: 'power2.out',
        stagger: 0.2,
    })

    tl.fromTo([heroTitleRef.value, heroSecondTitleRef.value, heroThirdTitleRef.value], {
        opacity: 0,
    }, {
        opacity: 1,
        duration: 0.6,
        stagger: 0.2,
        ease: 'linear',
    }, "<+=0.6")

    tl.fromTo([heroContentOneRef.value, heroContentTwoRef.value, heroContentThreeRef.value, heroContentFourRef.value, heroContentFiveRef.value, heroContentSixRef.value, heroContentSevenRef.value, heroContentEightRef.value, heroContentNineRef.value], {
        opacity: 0,
    }, {
        opacity: 1,
        duration: 0.7,
        ease: "linear",
        stagger: 0.1,
    },"<")
})
</script>

<style scoped lang="scss">
.hero{
    padding: 8rem;
    grid-template-rows: repeat(4, 1fr);
    min-height: 100vh;

    .key-words-desktop{
        display: none;
        grid-row: 2;

        @include tablet{
            display: block;
        }
    }

    .hero-content-container{
        grid-row: 2;
    }

    .hero-title{
        font-size: 12rem;
        color: $white;
        margin-bottom: 24px;
        @include ppneuemontreal(700);
    }

    .hero-content{
        font-size: 18rem;
        color: $white;
        opacity: 0.6;
        @include instrumentserif(400);
    }

    p{
        font-size: 16rem;
        color: $white;
        opacity: 0.6;
        @include instrumentserif(400);
    }

    ul{
        list-style: none;
        padding: 0;
        margin: 0;

        li{
            margin-bottom: 10px;
        }
    }
    .key-words-mobile{
        grid-row: 3;
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
        
        @include tablet{
            display: none;
        }
    }
        
}
</style>