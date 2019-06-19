<template>
    <div id="app">
        <h1>Choose your weapon !</h1>
        <div class="container">
            <scoreboard :score="score" @resetScoreEvent="resetScore" />
            <choices @makeChoiceEvent="playRound" v-show="!resultWindow.show" />
            <result-window :rw="resultWindow" @playAgainEvent="newRound" v-show="resultWindow.show" />
        </div>
    </div>
</template>

<script>
    import Scoreboard from './components/Scoreboard'
    import Choices from './components/Choices'
    import ResultWindow from './components/ResultWindow'

    export default {
        name: 'app',
        components: { Scoreboard, Choices, ResultWindow },
        data () {
            return {
                score: {
                    player: 0,
                    cpu: 0
                },
                resultWindow: {
                    text: '',
                    show: false
                }
            }
        },
        methods: {
            resetScore() {
                let reset = confirm('Are you sure you want to reset?');
                if(reset){
                    this.score = { player: 0, cpu: 0};
                }

            },
            playRound(playerChoice) {
                let cpuChoice = Math.floor(Math.random() * 3);

                //compare choices - determine winner
                if(playerChoice == cpuChoice) {
                    this.showResult('draw');
                } else if ((playerChoice - cpuChoice + 3) % 3 == 1) {
                    this.showResult('win');
                } else {
                    this.showResult('lose');
                }
            },
            showResult(result) {
                //show result window
                this.resultWindow.show = true;

                switch(result) {
                    case 'draw':
                        this.resultWindow.text = 'It is a tie!'
                    break;

                    case 'win':
                        this.resultWindow.text = 'You Win !'
                        this.score.player ++;
                    break;

                    case 'lose':
                        this.resultWindow.text = 'You Lose !'
                        this.score.cpu ++;
                    break;
                }
            },
            newRound() {
                this.resultWindow.show = false;
            }
        }
    }
</script>

<style lang="scss">
#app {
    background-image: linear-gradient(to right
    top, #440b2c, #500d33, #5d0f3a,
    #6a1041, #771248, #711444, #6c1540,
    #66163c, #4d152d, #351220,
    #1f0d13, #000000);
    height: 100vh;
        h1 {
            color:white;
            text-align:center;
        }
}
</style>
