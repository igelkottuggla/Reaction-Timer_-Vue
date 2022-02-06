<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      Click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
    .block {
        width: 30%;
        border-radius: 20px;
        background-image: url('../assets/block-bg.png');
        background-size: cover;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
        cursor: pointer;
    }
</style>