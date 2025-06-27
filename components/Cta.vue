<template>
  <component
    :is="isLink ? 'a' : 'button'"
    :href="isLink ? link : undefined"
    class="cta"
  >
    {{ text }}
    <svg width="6" height="6" viewBox="0 0 6 6" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" clip-rule="evenodd" d="M0.706523 0.654888C0.586107 0.775299 0.586107 0.970523 0.706523 1.09093L4.80517 5.18958H2.15788C1.98759 5.18958 1.84955 5.32766 1.84955 5.49792C1.84955 5.66818 1.98759 5.80625 2.15788 5.80625H5.54955C5.63132 5.80625 5.70976 5.77375 5.7676 5.71597C5.82538 5.65813 5.85788 5.57969 5.85788 5.49792V2.10624C5.85788 1.93596 5.71981 1.79791 5.54955 1.79791C5.37928 1.79791 5.24121 1.93596 5.24121 2.10624V4.75354L1.14257 0.654882C1.02216 0.534472 0.826934 0.534472 0.706523 0.654888Z" fill="white"/>
    </svg>
  </component>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  text: {
    type: String,
    required: true
  },
  link: {
    type: String,
    default: null
  }
})

const isLink = computed(() => !!props.link)
</script>

<style lang="scss" scoped>
.cta {
    @include ppneuemontreal(700);
    text-transform: uppercase;
    font-size: 7rem;
    padding: 12rem 26rem;
    background-color: $black;
    color: $white;
    cursor: pointer;

    @include tablet{
        font-size: 10rem;
    }

    svg{
        width: 6rem;
        height: 6rem;
        margin-left: 8rem;
    }
}
</style>
