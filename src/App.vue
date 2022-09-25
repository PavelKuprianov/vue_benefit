<template>
  <div id="app">
    <h1>Давайте выберем, что выгоднее</h1>
    <form class="form">
      <h2>Первый товар</h2>
      <div class="product__input">
        <input @blur="validator(price1)" class="product__inut_inp" type="text" placeholder="Стоимость первого товара" v-model.number="price1" required>
        <input @blur="validator(quantity1)" class="product__inut_inp" type="text" placeholder="Количество (объём) товара" v-model.number="quantity1" required>
      </div>

      <hr>
      <h2>Второй товар</h2>
      <div class="product__input">
        <input @blur="validator(price2)" class="product__inut_inp" type="text" placeholder="Стоимость второго товара" v-model.number="price2" required>
        <input @blur="validator(quantity2)" class="product__inut_inp" type="text" placeholder="Количество (объём) товара" v-model.number="quantity2" required>
      </div>
      <button type="button" @click.prevent="calculate">Посчитать</button>
    </form>

    <div class="result">
      <p>{{result}}</p>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      price1: '',
      quantity1: '',
      price2: '',
      quantity2: '',
      result: '',
    };
  },
  components: {
  },
  methods: {
    validator(value) {
      if(typeof value !== 'number') {
        this.value = ""
        alert('Вы ввели некорректное значение!')
      }

    },
    calculate() {
      if(this.price1 && this.quantity1 && this.price2 && this.quantity2) {
        this.result = this.price1 + this.price2;
      }
      
    }
  }
}
</script>

<style>
h2 {
  margin-bottom: 10px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
}
.form {
  margin: 0 auto;
  width: 100%;
}
.product__input {
  margin: 10px auto;
  display: flex;
  flex-direction: column;
  max-width: 300px;
  width: 100%;
}
.product__inut_inp {
  margin-bottom: 10px;
  font-size: 18px;
}
</style>
