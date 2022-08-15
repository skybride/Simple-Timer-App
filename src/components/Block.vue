<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
    </div>
</template>

<script>
    export default {
    props: ['delay'],
    components: { },
    data(){
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted(){
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer();
        }, this.delay)
        console.log(this.delay)
    },
    methods: {
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            }, 10);
        },
        stopTimer(){
            clearInterval(this.timer);
            this.$emit('score', this.reactionTime);
        }
    }
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background-color: palevioletred;
        color: snow;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>