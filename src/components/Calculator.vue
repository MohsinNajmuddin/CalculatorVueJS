<template>
  <div>
    <h1>{{ msg }}</h1>
    
    <input class="spacing" v-model="num1" placeholder="Enter a number" type="number">

    <select class="spacing" v-model="operation">
      <option disabled value="">Please select the operation to perform</option>
      <option>+</option>
      <option>-</option>
      <option>/</option>
      <option>*</option>
    </select>

    <input class="spacing" v-model="num2" placeholder="Enter a number" type="number">

    <button class="spacing"  v-on:click="calculate()">Calculate</button>

    <br/>

    <h3 v-if="!loading">Result: {{ this.result }}</h3>
    <h3 v-if="loading">Calculating Result ..............</h3>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      result: 0,
      num1: 0,
      num2: 0,
      operation: '',
      loading: false
    }
  },
  props: {
    msg: String
  },
  updated() {
    setTimeout(() => {
        this.loading = false;
    }, 5000);
  },

  methods: {
    calculate: function () {
      this.loading = true;
      switch (this.operation) {
        case '+':
          this.result = parseInt(this.num1) + parseInt(this.num2);
          break;
        case '-':
          this.result = parseInt(this.num1) - parseInt(this.num2);
          break;
        case '/':
          this.result = parseInt(this.num1) / parseInt(this.num2);
          break;
        case '*':
          this.result = parseInt(this.num1) * parseInt(this.num2);
          break;
      }
    }
  },
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.spacing {
  margin-left: 10px;
}


</style>
