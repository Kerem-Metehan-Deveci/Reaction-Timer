<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me Please
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
                this.Timer = setInterval(() => {
                    this.reactionTime += 10
                }, 10)
            },
            stopTimer() {
                clearInterval(this.Timer)
                this.$emit('end', this.reactionTime)
            }
        }
    }
</script>

<style scoped>
    .block {
        width: 400px;
        border-radius: 20px;
        background: rgb(34,193,195);
        background: linear-gradient(0deg, rgba(34,193,195,1) 0%, rgba(253,187,45,1) 100%);
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
        cursor: pointer;
    }
</style>