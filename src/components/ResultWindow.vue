<template>
    <div class="card" >
        <div class="card-body text-center">
            <h3 class="card-title">{{ rw.text }}</h3>
            <button class="hvr-pulse btn btn-primary" @click="playAgain">Play Again</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ResultWindow',
        props: ['rw'],
        data () {
            return {}
        },
        methods : {
            playAgain () {
                this.$emit('playAgainEvent');
            }
        }
    }
</script>
<style lang="scss">
    .hvr-pulse {
        display: inline-block;
        vertical-align: middle;
        -webkit-transform: perspective(1px) translateZ(0);
        transform: perspective(1px) translateZ(0);
        box-shadow: 0 0 1px rgba(0, 0, 0, 0);
    }
</style>
