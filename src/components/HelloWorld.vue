<template>
  <div class="hello">
    <input type="number" v-model.number="operand1" />
    <input type="number" v-model.number="operand2" />
    <button @click="getSum">+</button>
    <button @click="getDiffOperrands">-</button>
    <button @click="getResultDevidion">/</button>
    <button @click="getProductOperands">*</button>
    <button @click="getResultExponentiationOperands">**</button>
    <button @click="getResultIntegerDivision">Math.trunc</button>
    <p class="result">Result: {{ result }}</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: () => ({
    operand1: 0,
    operand2: 0,
    result: 0
  }),
  methods: {
    getSum () {
      this.result = this.operand1 + this.operand2
    },
    getDiffOperrands () {
      this.result = this.operand1 - this.operand2
    },
    getProductOperands () {
      this.result = this.operand1 * this.operand2
    },
    getResultDevidion () {
      this.result = this.operand1 / this.operand2
    },
    getResultExponentiationOperands () {
      this.result = Math.pow(this.operand1, this.operand2)
    },
    getResultIntegerDivision () {
      this.result = Math.trunc(this.operand1 / this.operand2)
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
</style>
