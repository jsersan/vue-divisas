<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h1>Vue JS Cambio de Divisas</h1>
  <div class="container">
    <div class="container-one">
      <select name="primera-divisa" id="primera-divisa" v-model="currency_one">
        <option value="AED">AED</option>
        <option value="ARS">ARS</option>
        <option value="AUD">AUD</option>
        <option value="BGN">BGN</option>
        <option value="BRL">BRL</option>
        <option value="BSD">BSD</option>
        <option value="CAD">CAD</option>
        <option value="CHF">CHF</option>
        <option value="CLP">CLP</option>
        <option value="CNY">CNY</option>
        <option value="COP">COP</option>
        <option value="CZK">CZK</option>
        <option value="DKK">DKK</option>
        <option value="DOP">DOP</option>
        <option value="EGP">EGP</option>
        <option value="EUR">EUR</option>
        <option value="FJD">FJD</option>
        <option value="GBP">GBP</option>
        <option value="GTQ">GTQ</option>
        <option value="HKD">HKD</option>
        <option value="HRK">HRK</option>
        <option value="HUF">HUF</option>
        <option value="IDR">IDR</option>
        <option value="ILS">ILS</option>
        <option value="INR">INR</option>
        <option value="ISK">ISK</option>
        <option value="JPY">JPY</option>
        <option value="KRW">KRW</option>
        <option value="KZT">KZT</option>
        <option value="MXN">MXN</option>
        <option value="MYR">MYR</option>
        <option value="NOK">NOK</option>
        <option value="NZD">NZD</option>
        <option value="PAB">PAB</option>
        <option value="PEN">PEN</option>
        <option value="PHP">PHP</option>
        <option value="PKR">PKR</option>
        <option value="PLN">PLN</option>
        <option value="PYG">PYG</option>
        <option value="RON">RON</option>
        <option value="RUB">RUB</option>
        <option value="SAR">SAR</option>
        <option value="SEK">SEK</option>
        <option value="SGD">SGD</option>
        <option value="THB">THB</option>
        <option value="TRY">TRY</option>
        <option value="TWD">TWD</option>
        <option value="UAH">UAH</option>
        <option value="USD">USD</option>
        <option value="UYU">UYU</option>
        <option value="VND">VND</option>
        <option value="ZAR">ZAR</option>
      </select>
      <input type="number" name="input-uno" id="input-uno" 
             v-model="amountOne" @change="fetchData()"/>
    </div>
    <div class="container-two">
      <button @click="switchValues()">Cambiar</button>
      <h4 id="valor-base">1 {{currency_one}} = {{rate}} {{ currency_two}} </h4>
    </div>
    <div class="container-three">
      <select name="segunda-divisa" id="segunda-divisa" v-model="currency_two">
        <option value="AED">AED</option>
        <option value="ARS">ARS</option>
        <option value="AUD">AUD</option>
        <option value="BGN">BGN</option>
        <option value="BRL">BRL</option>
        <option value="BSD">BSD</option>
        <option value="CAD">CAD</option>
        <option value="CHF">CHF</option>
        <option value="CLP">CLP</option>
        <option value="CNY">CNY</option>
        <option value="COP">COP</option>
        <option value="CZK">CZK</option>
        <option value="DKK">DKK</option>
        <option value="DOP">DOP</option>
        <option value="EGP">EGP</option>
        <option value="EUR">EUR</option>
        <option value="FJD">FJD</option>
        <option value="GBP">GBP</option>
        <option value="GTQ">GTQ</option>
        <option value="HKD">HKD</option>
        <option value="HRK">HRK</option>
        <option value="HUF">HUF</option>
        <option value="IDR">IDR</option>
        <option value="ILS">ILS</option>
        <option value="INR">INR</option>
        <option value="ISK">ISK</option>
        <option value="JPY">JPY</option>
        <option value="KRW">KRW</option>
        <option value="KZT">KZT</option>
        <option value="MXN">MXN</option>
        <option value="MYR">MYR</option>
        <option value="NOK">NOK</option>
        <option value="NZD">NZD</option>
        <option value="PAB">PAB</option>
        <option value="PEN">PEN</option>
        <option value="PHP">PHP</option>
        <option value="PKR">PKR</option>
        <option value="PLN">PLN</option>
        <option value="PYG">PYG</option>
        <option value="RON">RON</option>
        <option value="RUB">RUB</option>
        <option value="SAR">SAR</option>
        <option value="SEK">SEK</option>
        <option value="SGD">SGD</option>
        <option value="THB">THB</option>
        <option value="TRY">TRY</option>
        <option value="TWD">TWD</option>
        <option value="UAH">UAH</option>
        <option value="USD">USD</option>
        <option value="UYU">UYU</option>
        <option value="VND">VND</option>
        <option value="ZAR">ZAR</option>
      </select>
      <input type="number" name="input-dos" id="input-dos" placeholder="0" 
            v-model="amountTwo" disabled />
      <div class="container-four">
        <h4 id="ultimocambio">{{data.time_last_update_utc }}</h4>
      </div>

    </div>

  </div>
</template>

<script>

// let divisas = ["AED", "ARS", "AUD", "BGN", "BRL","BSD", "CAD","CHF","CLP","CNY","COP","CZK","DKK",
//               "DOP","EGP","EUR","FJD","GBP","GTQ","HKD","HRK","HUF","IDR","ILS","INR","ISK","JPY",
//               "KRW","KZT","MXN","MYR","NOK","NZD","PAB","PEN","PHP","PKR","PLN","PYG","RON","RUB",
//               "SAR","SEK", "SGD","THB","TRY","TWD","UAH","USD","UYU","VND","ZAR"];
               
export default {
  data() {
    return {
      data: [],
      currency_one: "USD",
      currency_two: "EUR",
      rate: "",
      amountOne: 1,
      amountTwo: 0,
    };
  },

  methods: {
    fetchData() {
      fetch(
        `https://v6.exchangerate-api.com/v6/${"9809b1cec3fb53ce2b3f3f6a"}/latest/${
          this.currency_one
        }`
      )
        .then((res) => res.json())
        .then((data) => {
          this.data = data;
          console.log(data);
          this.rate = data.conversion_rates[this.currency_two];
          this.amountTwo = this.amountOne * this.rate.toFixed(2);
        });
    },
    switchValues(){
      const valorTemporal = this.currency_one;
      this.currency_one = this.currency_two;
      this.currency_two = valorTemporal;
      this.fetchData();
    }
  },
    
    mounted() {  // Cuando está cargado montamos la data
      this.fetchData();
    },
  };


</script>

<style>
html {
  background: f4f4f4f4;
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  align-content: center;
  width: 100%;
  height: 100%;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

img {
  width: 150px;
}

.container {
  width: 50%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-content: center;
  align-items: center;
  text-align: center;
}

.container-two {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 50%;
}

.container-two button {
  padding: 5px;
  font-size: 12px;
  background-color: rgb(43, 98, 43);
  color: white;
  width: 30%;
  height: 10%;
  border: none;
  outline: none;
}

select {
  padding: 5px;
  /* width: 30%; */
  margin: 5px;
  border: 1px solid rgba(0, 0, 0, 0.5);
  outline: none;
}

input {
  padding: 5px;
  margin: 5px;
  font-size: 18px;
  border: 1px solid rgba(0, 0, 0, 0.5);
  outline: none;
}

#ultimocambio {
  font-weight: 500;
}

#valor-base {
  font-weight: 500;
}
</style>
