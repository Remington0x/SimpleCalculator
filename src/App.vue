<template>
    <div class="box">
    <h1 v-if="message === ''">{{counter}}</h1>
    <div v-else class="message">{{message}}</div>
    </div>
    <a class="buttons" v-on:click="printZero">0</a>
    <a class="buttons" v-on:click="printOne">1</a>
    <a class="buttons" v-on:click="printTwo">2</a>
    <a class="buttons" v-on:click="printThree">3</a>
    <br>
    <a class="buttons" v-on:click="printFour">4</a>
    <a class="buttons" v-on:click="printFive">5</a>
    <a class="buttons" v-on:click="printSix">6</a>
    <a class="buttons" v-on:click="printSeven">7</a>
    <br>    
    <a class="buttons" v-on:click="printEight">8</a>
    <a class="buttons" v-on:click="printNine">9</a>
    <a class="buttons" v-on:click="plus">+</a>
    <a class="buttons" v-on:click="minus">-</a>
    <br>    
    <a class="buttons" v-on:click="multiply">*</a>
    <a class="buttons" v-on:click="divide">/</a>
    <a class="buttons" v-on:click="calculate">=</a>
    <a class="buttons" v-on:click="clear">C</a>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
let a: number
enum EnumAction {
    noAction,
    plus,
    minus,
    divide,
    multiply,
}
let action: EnumAction = EnumAction.noAction

export default defineComponent({
    name: 'App',
    data() {
        return {
            counter: 0 as number,
            message: ''
        }
    },
    methods: {
        printZero() {
            this.counter = this.counter * 10
        },
        printOne() {
            this.counter = this.counter * 10 + 1
        },
        printTwo() {
            this.counter = this.counter * 10 + 2
        },
        printThree() {
            this.counter = this.counter * 10 + 3
        },
        printFour() {
            this.counter = this.counter * 10 + 4
        },
        printFive() {
            this.counter = this.counter * 10 + 5
        },
        printSix() {
            this.counter = this.counter * 10 + 6
        },
        printSeven() {
            this.counter = this.counter * 10 + 7
        },
        printEight() {
            this.counter = this.counter * 10 + 8
        },
        printNine() {
            this.counter = this.counter * 10 + 9
        },
        clear() {
            this.counter = 0
            this.message = ''
            action = EnumAction.noAction
        },
        plus() {
            a = this.counter
            this.counter = 0
            action = EnumAction.plus
        },
        minus() {
            a = this.counter
            this.counter = 0
            action = EnumAction.minus
        },
        divide() {
            a = this.counter
            this.counter = 0
            action = EnumAction.divide
        },
        multiply() {
            a = this.counter
            this.counter = 0
            action = EnumAction.multiply
        },
        calculate() {
            switch(action) {
                case EnumAction.plus: {
                    this.counter = a + this.counter;
                    break;
                }
                case EnumAction.minus: {
                    this.counter = a - this.counter;
                    break;
                }
                case EnumAction.divide: {
                    if (this.counter === 0) {
                        this.message = 'Error: divided by zero';
                        break;
                    } else {
                        this.counter = a / this.counter;
                        break;
                    }
                }
                case EnumAction.multiply: {
                    this.counter = a * this.counter;
                    break;
                }
                default: {
                    this.message = 'Error: no action specified'
                }
            }
        }
    }
});

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}

a.buttons {
  width: 60px;
  height: 50px;
  text-decoration: none;
  padding-top: 9px;
  color: #010101;
  text-align: center;
  line-height: 10px;
  display: inline-block;
  font: normal 17px arial;
}

a.buttons:not(.active) {
    border: 1px solid gray;
    background-image: linear-gradient(#f0f0f0, #c6c6c7);
    /* text-shadow: 0 0 21px rgba(223, 206, 228, 0.5), 0 -1px 0 #b2aabb; */
}

a.buttons:not(.active):hover,
a.buttons:not(.active):focus {
  transition: color 100ms linear;
  color: #fff;
  /* text-shadow: 0 0 21px rgba(223, 206, 228, 0.5), 0 0 10px rgba(223, 206, 228, 0.4), 0 0 2px #2a153c; */
}
a.buttons:not(:hover) {
    transition: 0.6s;
}

div.box {
    width: 234px;
    height: 70px;
    color: #333333;
    border: 2px solid gray;
    padding-right: 10px;
    text-align: right;
}

div.message {
    color: red;
    padding-top: 10px;
    font: normal 20px monospace;
    text-align: center;
}
</style>
