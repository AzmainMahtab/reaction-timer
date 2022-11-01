<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <h2>click me!</h2>
  </div>
</template>

<script>
export default {
    props: ["delay"],
    data () {
        return {
            showBlock : false,
            timer : null,
            reactionTime : 0,
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
            console.log(this.reactionTime)
        }
    }
}
</script>

<style scoped>
    .block {
        background-color: rgb(0, 255, 200);
        color: azure;
        text-align: center;
        padding: 100px 0%;
        border-radius: 20px;
        width: 400px;
        margin: 40px auto;
        cursor: pointer;
    }
</style>