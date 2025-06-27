<template>
    <section class="archives">
        <MenuBottom />
        <div class="grid-item" :class="{'empty': item.title === ''}" v-for="item in items" :key="item.title">
            <div v-if="item.month" class="month">{{ item.month }}</div>
            <div class="background" :style="{ backgroundColor: item.color }">
                <img v-if="item.image" :src="item.image" alt="image">
            </div>
            <div v-if="item.date" class="date">{{ item.date }}</div>
            <div v-if="item.title" class="wrapper-bottom">
                <h2 class="title">{{ item.title }}</h2>
                <div class="team">{{ item.team }}</div>
            </div>
        </div>
        <div class="grid-item hide-tablet"></div>
        <div class="grid-item hide-tablet"></div>
        <div class="grid-item hide-mobile"></div>
        <button class="grid-item button inactive hide-mobile">
            <span>2024</span>
        </button>
        <div class="grid-item hide-mobile"></div>
        <button class="grid-item button hide-mobile">
            <span>2025</span>
        </button>
        <div class="grid-item hide-mobile"></div>
        <div class="grid-item hide-mobile"></div>
    </section>
</template>

<script setup>
import placeholder from '@/public/images/placeholder.png'
import MenuBottom from '@/components/MenuBottom.vue';
import gsap from 'gsap';

const items = [
    {
        title: "",
        color: "",

    },
    {
        title: "",
        color: "",
    },
    {
        title: "",
        color: "",
    },
    {
        title: "",
        color: "",
    },
    {
        title: "",
        color: "",
    },
    {
        title: "",
        color: "",
    },
    {
        title: "",
        color: "",
    },
    {
        title: "",
        color: "",
    },
    {
        title: "",
        color: "",
    },
    {
        title: "",
        color: "",
    },
    {
        title: "GreenLife",
        date: "11/08/24",
        image: placeholder,
        color: "#414E3C",
        team:"(6 teams)",
        month: "january",
    },
    {
        title: "Orangina",
        date: "20/08/24",
        image: placeholder,
        color: "#F4F1EC",
        team:"(6 teams)",
        month: "",
    },
    {
        title: "Blueberry",
        date: "20/08/24",
        color: "#414E3C",
        team:"(6 teams)",
        month: "february",
    },
    {
        title: "Blueberry",
        date: "20/08/24",
        image: placeholder,
        color: "#414E3C",
        team:"(6 teams)",
        month: "",
    },
    {
        title: "Blueberry",
        date: "20/08/24",
        color: "#414E3C",
        team:"(6 teams)",
        month: "march",
    },
    {
        title: "Blueberry",
        date: "20/08/24",
        image: placeholder,
        color: "#414E3C",
        team:"(6 teams)",
        month: "",
    },
    {
        title: "GreenLife",
        date: "11/08/24",
        image: placeholder,
        color: "#414E3C",
        team:"(6 teams)",
        month: "january",
    },
    {
        title: "Orangina",
        date: "20/08/24",
        image: placeholder,
        color: "#F4F1EC",
        team:"(6 teams)",
        month: "",
    },
    {
        title: "Blueberry",
        date: "20/08/24",
        color: "#414E3C",
        team:"(6 teams)",
        month: "february",
    },
    {
        title: "Blueberry",
        date: "20/08/24",
        image: placeholder,
        color: "#414E3C",
        team:"(6 teams)",
        month: "",
    },
    {
        title: "Blueberry",
        date: "20/08/24",
        color: "#414E3C",
        team:"(6 teams)",
        month: "march",
    },
    {
        title: "Blueberry",
        date: "20/08/24",
        image: placeholder,
        color: "#414E3C",
        team:"(6 teams)",
        month: "",
    },
    {
        title: "GreenLife",
        date: "11/08/24",
        image: placeholder,
        color: "#414E3C",
        team:"(6 teams)",
        month: "january",
    },
    {
        title: "Orangina",
        date: "20/08/24",
        image: placeholder,
        color: "#F4F1EC",
        team:"(6 teams)",
        month: "",
    },
]

onMounted(() => {
    const tl = gsap.timeline();
    
    tl.fromTo(".grid-item",
     {
        opacity: 0,
    }, {
        opacity: 1,
        duration: 0.8,
        ease: 'linear',
        stagger:{
            amount: 0.9,
            from: 'random',
            grid: "auto",
        }
    })
})
</script>

<style scoped lang="scss">
.archives{
    position: relative;
    overflow: hidden;
    padding: 8rem;
    display: grid;
	grid-template-columns: repeat(2, minmax(0, 1fr));
    background-color: #F4F1EC;
    gap:8rem;
    min-height: 100vh;

    @include tablet {
		grid-template-columns: repeat(6, minmax(0, 1fr));
	}

	@include desktop {
		grid-template-columns: repeat(8, minmax(0, 1fr));
	}

    .grid-item {
        position: relative;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        width: 100%;
        height: calc((100vh - 32rem) / 4);
        border: 1px solid rgb(#0000001A, 0.1);
        padding: 16rem;

        &.empty{
            display: none;

            @include tablet{
                display: flex;
            }

            &::before{
                content: "";
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                background:linear-gradient(
                    to bottom right, 
                    transparent  calc(50% - 0.5px), 
                    rgb(#0000001A, 0.1) calc(50% - 0.5px), 
                    rgb(#0000001A, 0.1) calc(50% + 0.5px), 
                    transparent  calc(50% + 0.5px) 
                )
            }
        }

        &.hide-tablet{
            display: none;
            @include desktop{
                display: flex;
            }
        }

        &.hide-mobile{
            display: none;

            @include tablet{
                display: flex;
            }
        }

        &.button{
            justify-content: flex-end;
            align-items: flex-start;
            padding: 0;

            &.inactive{
                span{
                    opacity: 0.45;
                }
            }
            
            span{
                @include ppneuemontreal(500);
                line-height: 0.7;
                font-size: 40rem;
                color: $black;

                @include tablet{
                    font-size: 46rem;
                }

                @include desktop{
                    font-size: 73rem;
                }
            }
        }

        .background{
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;

            img{
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
        }   

        .month{
            position: absolute;
            left: 0;
            bottom: 0;
            transform: translate3d(0, 100% , 0);
            @include ppneuemontreal(400);
            text-transform: uppercase;
            font-size: 10rem;
            color: #00000066;
            opacity: 0.4;
            height: fit-content;
        }

        .date{
            position: relative;
            @include ppneuemontreal(400);
            font-size: 10rem;
            color: $white;
        }

        .title{
            position: relative;
            @include instrumentserif(400 , italic);
            font-size: 28rem;
            color: $white;
            margin-bottom: 8rem;
        }

        .team{
            position: relative;
            @include ppneuemontreal(400);
            font-size: 10rem;
            color: $white;
            opacity: 0.5;
        }
    }
}
</style>