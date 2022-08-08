<template>
    <div class="container">
        <p>Your Reaction Speed is : <span>{{ score }}</span> ms</p>
        <h3 :class="{pepsi: message == 'What a Reaction', snail: message == 'Snail Pace ...'}">{{ message }}</h3>
    </div>
</template>

<script>
    export default {
        name: 'ResultBar',
        props: ['score', 'message']
    }
</script>

<style scoped>
    .container {
        margin-top: 30px;
        padding: 0 20px;
        border: 1px solid #000;
    }

    .snail {
        color: red;
    }

    .pepsi {
        color: green;
    }
</style>