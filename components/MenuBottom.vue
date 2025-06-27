<template>
    <div class="menu-bottom" ref="menuBottomRef">
        <div class="menu-bottom-item" v-for="item in items" :key="item.title">
            <nuxt-link :to="item.link" :class="{'active': $route.path === item.link}">{{ item.title }}</nuxt-link>
        </div>
    </div>
</template>

<script setup>
import { LOADER_PLAYED } from '@/utils/constant';
import gsap from 'gsap';

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

const route = useRoute();

const menuBottomRef = ref(null);

onMounted(() => {
    const delay = LOADER_PLAYED.PLAYED == 'true' || route.path !== '/' ? 1 : 5.5;

    const tl = gsap.timeline({
        delay: delay,
    });

    tl.fromTo(menuBottomRef.value, {
        y: 100,
    }, {
        y: 0,
        duration: 1.2,
        ease: 'power2.out',
    })

    tl.fromTo(menuBottomRef.value, {
        opacity: 0,
    }, {
        opacity: 1,
        duration: 0.6,
        ease: 'linear',
    },"<")
});
</script>

<style scoped lang="scss">
.menu-bottom{
    position: fixed;
    bottom: 8rem;
    left: 8rem;
    background-color: #FFFFFF;
    padding: 25rem 86rem 29rem 37rem;
    flex-wrap: wrap;
    gap: 20rem;
    width: 351rem;
    justify-content: space-between;
    display: none;
    z-index: 100;

    @include desktop{
        display: flex;
    }

    .menu-bottom-item{
        width: 86rem;

        &:hover{
            a{
                opacity: 1;

                &::before{
                    background-color: $black;
                }
            }
        }

        a{
            @include ppneuemontreal(500);
            font-size: 12rem;
            color: $black;
            position: relative;
            opacity: 0.3;
            padding-left: 20px;
            transition: opacity 0.3s linear;
            text-transform: uppercase;

            &::before{
                content: '';
                position: absolute;
                left: -20px;
                top: 50%;
                width: 7px;
                height: 7px;
                border: 1px solid $black;
                transform: translateY(-50%);
                transition: background-color 0.3s linear;
            }

            &.active{
                opacity: 1;

                &::before{
                    background-color: $black;
                }
            }
        }
    }
}
</style>