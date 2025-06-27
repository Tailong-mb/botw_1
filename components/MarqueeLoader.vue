<template>
    <div class="marquee-loader">
        <div class="first-line" :class="type">
            <img 
                v-for="(image, index) in images" 
                :key="`first-${index}`"
                :src="image" 
                :alt="`image-${index + 1}`"
            >
        </div>
        <div class="second-line" :class="type">
            <img 
                v-for="(image, index) in images" 
                :key="`second-${index}`"
                :src="image" 
                :alt="`image-${index + 1}`"
            >
        </div>
    </div>
</template>

<script setup>
defineProps({
    images: {
        type: Array,
        required: true,
        default: () => []
    },
    type: {
        type: String,
        default: 'top'
    }
})
</script>

<style lang="scss" scoped>
.marquee-loader {
    width: 100%;
    @keyframes loader-animation-top {
        0% {
            transform: translateY(0);
        }
        100% {
            transform: translateY(-100%);
        }
    }

    @keyframes loader-animation-bottom {
        0% {
            transform: translateY(-100%);
        }
        100% {
            transform: translateY(0);
        }
    }

    .first-line,
    .second-line {
        display: flex;
        flex-wrap: nowrap;
        flex-direction: column;
        gap: 8rem;
        padding-top: 8rem;

        &.top{
            animation: loader-animation-top 15s linear infinite;
        }

        &.bottom{
            animation: loader-animation-bottom 15s linear infinite;
        }
        
        img {
            width: 100%;
            height: auto;
            aspect-ratio: 182/240;
            object-fit: cover;
            opacity: 0;
        }
    }
}
</style>
