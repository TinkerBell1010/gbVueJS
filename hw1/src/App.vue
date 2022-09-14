<template>
  <div class="container">
    <div class="screen">
      <input type="number" v-model="operand1">
      <p>{{ operator }}</p>
      <input type="number" v-model="operand2">
      <p>=</p>
      <p>{{ result }}</p>
    </div>
    <div class="keyboard">
      <button @click="operator = '+'">+</button>
      <button @click="operator = '-'">-</button>
      <button @click="operator = '*'">*</button>
      <button @click="operator = '/'">/</button>
      <button @click="operator = '^'">^</button>
      <button @click="operator = ':'">:</button>
      <button @click="getResult">=</button>
    </div>
    <p class="notes">^ - возведение в степень</p>
    <p class="notes">: - целочисленное деление</p>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      operand1: 0,
      operand2: 0,
      operator: '+',
      result: 0
    }
  },
  methods: {
    getResult() {
      switch(this.operator) {
        case '+':
          this.result = +this.operand1 + +this.operand2;
          break;

        case '-':
          this.result = this.operand1 - this.operand2;
          break;

        case '*':
          this.result = this.operand1 * this.operand2;
          break;

        case '/':
          this.result = this.operand1 / this.operand2;
          break;

        case '^':
          this.result = Math.pow(this.operand1,this.operand2);
          break;

        case ':':
          this.result = Math.floor(this.operand1/this.operand2);
          break;


        default:
          this.result = 'err';
          break;
      }
    }
  }
  
}
</script>

<style lang="sass">
  body
   background-color: #938ACF

  .container
    max-width: 600px
    margin: 100px auto
    background-color: #552A7A
    padding: 70px
    border-radius: 30px

  .screen
    width: 100%
    display: flex
    justify-content: space-between
    align-items: center

  input
    padding: 5px 10px
    border-radius: 10px
    height: 30px
    font-size: 16px
    max-width: 150px
    color: #552A7A
    background-color: #F4F5F3

  p 
    font-size: 20px
    color: #F4F5F3

  .keyboard
    width: 100%
    display: flex
    justify-content: space-around
    margin: 40px 0

  button
    width: 50px
    height: 50px
    font-size: 20px
    background-color: #EAC251
    border-radius: 10px
    border: none
    color: #552A7A
    cursor: pointer
    transition: all .4s ease

    &:hover
     background-color: rgba(232, 194, 81, 0.8) 

  .notes
    font-size: 14px

</style>
