<template>
    <div class="card">
        <div class="card-body">
            <div class="row col-md-12">
                <div class="col text-center " v-for="(option, index) in options">
                    <button  class="btn btn-custom hvr-grow" @click="makeChoice(index)">
                        <i class="option" :class="'fa fa-hand-' + option + '-o'"></i>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'choices',
    data() {
        return {
            options: ['rock', 'paper', 'scissors']
        }
    },
    methods: {
        makeChoice(i) {
            this.$emit('makeChoiceEvent', i);
        }
    }
}
</script>

<style lang="scss">
    .btn-custom {
        background-color: #891451;
        color: white;
    }
    .option {
        font-size: 10rem;
    }
    .hvr-grow {
        display: inline-block;
        vertical-align: middle;
        -webkit-transform: perspective(0.10px) translateZ(0);
        transform: perspective(0.10px) translateZ(0);
        box-shadow: 0 0 1px rgba(0, 0, 0, 0);
        -webkit-transition-duration: 0.2s;
        transition-duration: 0.2s;
        -webkit-transition-property: transform;
        transition-property: transform;
    }

</style>
