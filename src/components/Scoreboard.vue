<template>
    <div class="card-body">
        <div class="row">
            <div class="col-4 text-center">Player Score: {{ score.player }}</div>
            <div class="col-4 text-center">
                <button class="btn btn-danger hvr-shrink" @click="resetScore">
                    <i class="fa fa-circle-o-notch fa-spin"></i>
                    Reset
                </button>
            </div>
            <div class="col-4 text-center">Cpu Score: {{ score.cpu }}</div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'scoreboard',
        props: ['score'],
        data () {
            return {

            }
        },
        methods: {
            resetScore() {
                this.$emit('resetScoreEvent');

            }
        }
    }
</script>

<style lang="scss">
    .card-body {
        background-color: #440B2C;
        color: white;
    }
    .hvr-float {
        display: inline-block;
        vertical-align: middle;
        -webkit-transform: perspective(0.5px) translateZ(0);
        transform: perspective(0.5px) translateZ(0);
        box-shadow: 0 0 1px rgba(0, 0, 0, 0);
        -webkit-transition-duration: 0.3s;
        transition-duration: 0.3s;
        -webkit-transition-property: transform;
        transition-property: transform;
        -webkit-transition-timing-function: ease-out;
        transition-timing-function: ease-out;
    }
</style>
