<template>
    <p class="resultData">Reaction time - {{time}}ms</p>
</template>

<script>
export default {
    proprs: ['time'],
    name: 'Results',
}
</script>

<style scoped>
    .resultData {
        font-size: 18px
    }
</style>