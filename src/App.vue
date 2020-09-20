<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
      <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
      <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul>
    <table class="table">
  <thead class="thead-light">
    <tr>
      <th scope="col">Jméno</th>
      <th scope="col">Příjmení</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="a in this.zaznamy"
    v-bind:key="a"
    >
    <td>
      {{a.Jmeno}}
    </td>
    <td>   
      {{a.Prijmeni}} 
    </td>  
    </tr>
  </tbody>
</table>
  </div>

</template>

<script>
const axios = require("axios")
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      zaznamy: [{Jmeno: "Jan", Prijmeni: "Novak"},
                {Jmeno: "Jan", Prijmeni: "Stary"}]
    }
  },
  methods:{dejdata(){
        this.msg = 'jjj';
          axios({
            method:"get",
            url:"http://127.0.0.1:3000",
          }).then(response => {
            this.zaznamy = response.data;
            console.log("funguju");
          }
          )
          .catch(error => {
            this.msg = error.message;
          })
  }
  },
  mounted(){
  this.dejdata();
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
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
</style>
