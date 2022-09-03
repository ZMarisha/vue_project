<template>
  <div class="hello">
    <p>{{ error }}</p>
    <input type="number" v-model.number="operand1"/>
    <input type="number" v-model.number="operand2"/>
    <button v-for="operator of operators" @click="calculator(operator)" :key="operator">{{ operator }}</button>
    <button type="reset" @click="reset">Reset</button>
    <p class="result">Result: {{ result }}</p>
    <label><input class="checkbox" type="checkbox" v-model="seen"/>Отобразить экранную клавиатуру</label>
    <br/>
    <div v-if="seen">
      <button v-for="number of numbers" :key="number" @click="change(number)">{{ number }}</button>
      <button @click="backspase">BackSpace</button>
      <br/>
      <label><input class="radio" type="radio" name="operand" value="operand1" v-model="radio"/>Операнд 1</label>
      <label class="label2"><input class="radio" name="operand" value="operand2" type="radio" v-model="radio"/>Операнд 2</label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: () => ({
    operand1: 0,
    operand2: 0,
    result: 0,
    operators: ['+', '-', '/', '*', '^', '%'],
    error: '',
    numbers: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
    seen: false,
    radio: 'operand1'
  }),
  methods: {
    calculator (operator) {
      this.error = ''
      switch (operator) {
        case '+': this.getSum(); break
        case '-': this.getDiffOperrands(); break
        case '/': this.getResultDevidion(); break
        case '*': this.getProductOperands(); break
        case '^': this.getResultExponentiationOperands(); break
        case '%': this.getResultIntegerDivision(); break
      }
    },
    getSum () {
      const { operand1, operand2 } = this
      this.result = operand1 + operand2
    },
    getDiffOperrands () {
      const { operand1, operand2 } = this
      this.result = operand1 - operand2
    },
    getProductOperands () {
      const { operand1, operand2 } = this
      this.result = operand1 * operand2
    },
    getResultDevidion () {
      const { operand1, operand2 } = this
      if (operand2 === 0) {
        this.error = 'На ноль делить нельзя!'
        return
      }
      this.result = operand1 / operand2
    },
    getResultExponentiationOperands () {
      const { operand1, operand2 } = this
      this.result = Math.pow(operand1, operand2)
    },
    getResultIntegerDivision () {
      const { operand1, operand2 } = this
      this.result = Math.trunc(operand1 / operand2)
    },
    reset () {
      this.operand1 = 0
      this.operand2 = 0
      this.result = 0
      this.error = ''
    },
    change (el) {
      const value = this[this.radio]
      console.log(this[this.radio])
      if (typeof value === 'number') {
        this[this.radio] = Number(`${value}${el}`)
      }
    },
    backspase () {
      const value = this[this.radio]
      if (typeof value === 'number') {
        this[this.radio] = Math.trunc(value / 10)
        console.log(this[this.radio])
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.result {
  color: green;
  font-weight: 600;
  font-size: 24px;
}
button {
  margin-left: 5px;
}
.checkbox {
width: 15px;
height: 15px;
margin-bottom: 20px;
}
.radio {
  margin-top: 20px;
}
.label2 {
  margin-left: 30px;
}
</style>
