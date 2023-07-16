<script>
import { ref } from 'vue';

export default {
  el: '#app',
  data() {
        return {
          result: '',
          numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
          operators: ['+','-', '*', '/'],
        };
      },
      methods: {
        appendNumber(num) {
          this.result += num;
        },
        performOperation(op) {
          this.result += ' ' + op + ' ';
        },
        clear() {
          this.result = '';
        },
        calculate() {
          try {
            this.result = eval(this.result);
          } catch (error) {
            this.result = 'Error';
          }
        }
      }
}
</script>

<template>
  <div id="app">
    <div class="calculator">
      <h2> Simple Calculator</h2>
    <input type="text" v-model="result" class="textbox" disabled>
    <br><br>
    <button class="button" v-for="num in numbers" :key="num" @click="appendNumber(num)">{{ num }}</button>
    <br><br>
    <button class="operators" v-for="op in operators" :key="op" @click="performOperation(op)">{{ op }}</button>
    <br><br>
    <button @click="clear">Clear</button>
    <button @click="calculate">Calculate</button>
    </div>
  </div>
</template>

<style>
  .calculator {
      display: grid;
      grid-template-columns: repeat(3, 10fr);
      grid-gap: 4px;
      max-width: 500px;
      margin: 0 auto;
      padding: 10px;
      border: solid black 5px;
      border-radius: 12px;
      background-color: #003cff54;
    }
    .button {
      padding: 10px;
      text-align: center;
      background-color: #00000000;
      cursor: pointer;
    }
    .button:hover {
      background-color: #73ddfd88;
    }
    .operators {
      padding: 10px;
      text-align: center;
      background-color: #00000000;
      cursor: pointer;
    }
    .operators:hover {
      background-color: #73ddfd4f;
    }
    .textbox {
      max-width: 300px;
      max-height: 60px;
      background-color: #9272e950;
    }
</style>
