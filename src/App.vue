<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>Region sekarang = {{ msg }}</h1>
    <button @click="changeMsg">ganti region</button>
    <br>
    <br>

    <select v-model="selected">
      <option v-for="product in products" v-bind:value="{id: product.id, text: product.name}" :key="product.id">
        {{ product.show }}
      </option>
    </select>
    <br>
    <br>
    <!-- <button @click="getTime">Get Time</button> -->
    <h1>
      {{ test.formatted }}
    </h1>
    <h2>{{ test.countryName }} {{ test.zoneName }}</h2>
  </div>
</template>

<script>
import axios from "axios";

export default {
  created() {
    this.getTime();
    setInterval(() => {
      this.getTime();
    }, 1000);
  },
  name: "App",
  data() {
    return {
      msg: "Asia/Jakarta",
      test: ["test"],
      link:
        "paste your api here" +
        this.param,
      param: "",
      linkDefault:
        "paste your api here",
      selected: "",
      products: [
        { id: 1, name: "Asia/Jakarta", show :"WIB" },
        { id: 2, name: "Asia/Jayapura" , show :"WIT"},
        { id: 3, name: "Asia/Makassar" , show :"WITA"},
      ],
    };
  },
  methods: {
    changeMsg() {
      
      this.msg = this.selected.text;
      this.linkDefault =
        "paste your api here" +
        this.selected.text;
    },
    getTime() {
      axios
        .get(this.linkDefault)
        .then((response) => {
          this.test = response.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
