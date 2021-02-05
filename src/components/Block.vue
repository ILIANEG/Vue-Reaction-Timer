<template>
    <div class="playArea">
        <div class="dot" :style="{bottom: x+'px', right: y+'px'}" v-if="!counting" @click="hit()"></div>
        <p class="counter" @load="countDown()" v-if="counting">{{ countdown }}</p>
    </div>
</template>

<script>
export default {
    name: 'Block',
    data() {
        return {
            x: Math.random() * (370 - 3) + 3,
            y: Math.random() * (370 - 3) + 3,
            countdown: 3,
            counting: true,
        }
    },
    methods: {
        hit() {
            this.$emit('hit');
        },
        countDown() {
            if (this,this.countdown>0) {
                setTimeout(() => {
                    this.countdown -= 1
                    this.countDown()
                },1000)
            } else {
                this.counting = false
                this.$emit('start')
            }
        }
    },
    created() {
        this.countDown()
    }
}
</script>

<style scoped>
    .playArea {
        margin: auto;
        margin-top: 20px;
        width: 400px;
        height: 400px;
        background-color:gainsboro;
        position: relative;
        border-radius: 10px;
    }
    .dot {
      width: 25px;
      height: 25px;
      background-color: rgb(0, 150, 219);
      border-radius: 100px;
      position: absolute;
    }
    .dot:hover {
        opacity: 100%;
        background-color: red;
    }
    .counter {
        font-size: 45px;
        position: absolute;
        top:35%;
        right: 45%;
        align-items: center;
        -moz-user-select: none;
        webkit-user-select: none;
        ms-user-select: none;
    }

</style>