<template>
    <div @click="stopTimer()">
        Click Me Now!
    </div>
</template>

<script>
    export default {
        name: 'BlockBar',
        data() {
            return {
                reactionTime: 0,
                timer: null
            }
        },
        methods: {
            startTimer() {
                this.reactionTime += 10;
                console.log(this.reactionTime);
            },
            stopTimer() {
                clearInterval(this.timer);
                console.log(this.reactionTime);
                this.$emit('haltPlay', this.reactionTime);
            }
        },
        mounted() {
            this.timer = setInterval(this.startTimer, 10);
        }
    }
</script>

<style scoped>
    div {
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        background-image: url(../assets/logo.png);
        background-position: center;
        background-repeat: no-repeat;
        color: black;
        font-size: 22px;
        width: 50%;
        max-width: 200px;
        padding: 30px;
        border: 1px solid black;
        border-radius: 20px;
        height: 150px;
        margin: 30px 0;
        cursor: pointer;
    }
</style>