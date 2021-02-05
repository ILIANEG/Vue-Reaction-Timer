<template>
    <p class="resultData">Reaction time - {{ time }}ms</p>
    <p class="identifier">{{ identify(time) }}</p>
</template>

<script>
import { computed } from 'vue'
export default {
    props: ['time'],
    name: 'Results',
    methods: {
        identify(time){
            if (1000 < time) {
                return 'waaay too slow'
            } else if (time < 650) {
                return 'lightning speed'
            } else {
                return 'average time'
            }
        }
    }
}
</script>

<style scoped>
    .resultData {
        font-size: 18px;
    }
    .identifier {
        font-weight: bold;
        font-size: 28px;
        color: rgb(0, 150, 219);
    }
</style>