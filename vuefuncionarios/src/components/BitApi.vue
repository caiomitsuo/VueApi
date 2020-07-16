<template>
  <div class="container">
    <h1 class="logo__text">Preços do Bitcoin</h1>
    <div v-for="currency in info" v-bind:key="currency" class="currency__name">
      {{ currency.description }}:
      <span class="value">
        <span v-html="currency.symbol"></span>
        {{ currency.rate_float | currencydecimal }}
      </span>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "BitApi",
  data () {
    return {
      info: null,
      loading: true,
      errored: false,
    };
  },
  filters: {
    currencydecimal(value) {
      return value.toFixed(2);
    },
  },
  mounted () {
    axios
      .get("https://api.coindesk.com/v1/bpi/currentprice.json")
      .then((response) => {
        this.info = response.data.bpi;
      })
      .catch((error) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  },
};
</script>

<style>
.container {
  width: 20vw;
}
.currency__name {
  color: black;
}
.value {
  color: green;
}
.logo__Text {
  color: #eff7f4;
}
</style>
