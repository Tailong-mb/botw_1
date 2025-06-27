<template>
    <header class="home-header container">
        <div class="wrapper col-start-1 col-end-3 tb:col-end-7 dk:col-end-6" ref="headerRef">
            <div class="menu-container" ref="menuContainerRef">
                <div class="menu-item" v-for="item in items" :key="item.title">
                    <nuxt-link :to="item.link" :class="{'active': $route.path === item.link}" @click="closeMenu">{{ item.title }}</nuxt-link>
                </div>
            </div>
            <img :src="logo" alt="logo" class="logo">
            <div class="right-part">
                <button class="menu-button" ref="menuButtonRef" @click="openMenu">
                    <svg width="9" height="9" viewBox="0 0 9 9" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <rect x="0.25" y="0.25" width="3.5" height="3.5" stroke="black" stroke-width="0.5"/>
                        <rect x="0.25" y="5.25012" width="3.5" height="3.5" stroke="black" stroke-width="0.5"/>
                        <rect x="5.25" y="0.25" width="3.5" height="3.5" stroke="black" stroke-width="0.5"/>
                        <rect x="5.25" y="5.25012" width="3.5" height="3.5" stroke="black" stroke-width="0.5"/>
                    </svg>
                    <span>Menu</span>
                </button>
                <button class="register-button" ref="registerButtonRef">
                    <img :src="twitch" alt="twitch" class="twitch-icon">
                    <span>CONNEXION</span>
                </button>
            </div>
        </div>
    </header>
</template>

<script setup>
import logo from '@/public/images/logo.png'
import twitch from '@/public/images/twitch.png'
import gsap from 'gsap';
import { LOADER_PLAYED } from '@/utils/constant';

const items = [
    {
        title: 'Home',
        link: '/'
    },{
        title: 'Briefs',
        link: '/briefs'
    },{
        title: 'Archives',
        link: '/archives'
    },{
        title: 'Credits',
        link: '/credits'
    },
]

const headerRef = ref(null);
const registerButtonRef = ref(null);
const menuButtonRef = ref(null);
const menuContainerRef = ref(null);
const route = useRoute();
const isMenuOpen = ref(false);

let tlMenu = null;

onMounted(() => {
    const delay = LOADER_PLAYED.PLAYED == 'true' || route.path !== '/' ? 0 : 4.5;

    const tl = gsap.timeline({delay: delay});

    tl.fromTo([headerRef.value, menuButtonRef.value, registerButtonRef.value], {
        opacity: 0,
    }, {
        opacity: 1,
        duration: 0.5,
        ease: "linear",
        stagger: 0.1,
    })

    document.addEventListener('click', handleClickOutside);
})

onUnmounted(() => {
    document.removeEventListener('click', handleClickOutside);
})

const handleClickOutside = (event) => {
    if (isMenuOpen.value && menuContainerRef.value && !menuContainerRef.value.contains(event.target) && !menuButtonRef.value.contains(event.target)) {
        closeMenu();
    }
}

const openMenu = () => {
    isMenuOpen.value = true;
    tlMenu?.kill();

    tlMenu = gsap.timeline();

    tlMenu.to([menuButtonRef.value, registerButtonRef.value], {
        xPercent: 110,
        duration: 0.7,
        ease: "power2.out",
        stagger: 0.1,
    })

    tlMenu.to(menuContainerRef.value, {
        yPercent: 0,
        y: 0,
        duration: 0.8,
        ease: "power2.out",
    }, 0.3)
}

const closeMenu = () => {
    isMenuOpen.value = false;
    tlMenu?.kill();

    tlMenu = gsap.timeline();

    tlMenu.to(menuContainerRef.value, {
        yPercent: -100,
        duration: 0.8,
        ease: "power2.out",
    })

    tlMenu.to([registerButtonRef.value, menuButtonRef.value], {
        xPercent: 0,
        duration: 0.7,
        ease: "power2.out",
        stagger: 0.1,
    },0.3)
}

</script>

<style lang="scss" scoped>
.home-header {
    position: fixed;
    top: 0;
    z-index: 100;
    width: 100%;

    .wrapper{
        padding: 8rem 8rem 0 8rem;
        display: flex;
        justify-content: space-between;
        align-items: flex-start;

        @include desktop{
            padding: 8rem 3rem 0 8rem;
        }

        .menu-container{
            position: absolute;
            top: 0;
            right: 0;
            height: 100rem;
            width: 100%;
            padding: 25rem 86rem 29rem 37rem;
            background: $black;
            display: flex;
            gap: 20rem;
            justify-content: space-between;
            flex-wrap: wrap;
            transform: translate3d(0, -100%, 0);

            @include tablet{
                max-width: 370rem;
            }

            @include desktop{
                display: none;
            }

            .menu-item{
                width: 28%;

                &:hover{
                    a{
                        opacity: 1;

                        &::before{
                            background-color: #FFFFFF;
                        }
                    }
                }

                a{
                    @include ppneuemontreal(500);
                    font-size: 12rem;
                    color: #FFFFFF;
                    position: relative;
                    opacity: 0.3;
                    padding-left: 20px;
                    transition: opacity 0.3s linear;

                    &::before{
                        content: '';
                        position: absolute;
                        left: -20px;
                        top: 50%;
                        width: 7px;
                        height: 7px;
                        border: 1px solid #FFFFFF;
                        transform: translateY(-50%);
                        transition: background-color 0.3s linear;
                    }

                    &.active{
                        opacity: 1;

                        &::before{
                            background-color: #FFFFFF;
                        }
                    }
                }
            }
        }

        .logo{
            width: 132px;

            @include tablet{
                width: 100px;
            }
        }

        .right-part{
            display: flex;
            flex-direction: column;
            align-items: flex-end;
            gap: 8rem;
        }

        .register-button,
        .menu-button{
            display: flex;
            align-items: center;
            padding: 15px 20px;
            gap: 8px;
            background-color: $white;
            color: $black;
            width: fit-content;

            @include desktop{
                margin-top: 0;
            }

            span{
                @include ppneuemontreal(500);
                font-size: 12rem;
            }
        }

        .menu-button{
            @include desktop{
                display: none;
            }
        }
    }
}
</style>