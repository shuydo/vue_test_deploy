<script>
import axios from "axios";
export default {
  name: "Stocks",
  data() {
    return {
      stock: [],
      errors: [],
      selected: "",
    };
  },
  //uses Anna key
  created() {
    axios
      .get(
        "https://financialmodelingprep.com/api/v3/profile/AAPL,NVDA,TSLA,INTC,MDB,V,DAL,DOCU,OKTA,AMZN,PINS,TRIP,GDDY,MCD,NOK,UPWK,FB,OZON,NFLX,EA,HLT,H,CCL,AMD,SPCE,IBM,ZM,DIS?apikey=6c9be8fcb7df7894ba5ae48be14935fc"
      )
      .then(resp => (this.stock = resp.data))
      .catch(err => this.errors.push(err));
  },
};
</script>

<template>
  <div class="stock">
    <div class="stock-item" v-for="value in stock" :key="value.stock">
      <div class="stock-item__cover">
        <img :src="value.image" :alt="value.companyName" />
      </div>

      <h3 class="stock-item__title">
        {{ value.companyName }}
        <span>{{ value.symbol }}</span>
      </h3>

      <span class="stock-item__price">{{ value.price }} $</span>
    </div>
  </div>

  <h3>Get Info</h3>
  <select v-model="selected">
    <option value="" disabled>Select Company</option>
    <option
      v-for="value in stock"
      :key="value.stock"
      :value="value.description"
    >
      {{ value.companyName }}
    </option>
  </select>

  <div class="info">{{ selected }}</div>
</template>
