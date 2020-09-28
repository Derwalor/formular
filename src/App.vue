<template>
  <div id="app">
    <table class="table">
  <thead class="thead-light">
    <tr>
      <th scope="col">Jméno</th>
      <th scope="col">Příjmení</th>
      <th scope="col">E-mail</th>
      <th scope="col">Telefon</th>
      <th scope="col">Ulice</th>
      <th scope="col">Město</th>
      <th scope="col">PSČ</th>
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
    <td>   
      {{a.Email}} 
    </td>
    <td>   
      {{a.Telefon}} 
    </td>
    <td>   
      {{a.Ulice}} 
    </td>  
    <td>   
      {{a.Mesto}} 
    </td>  
    <td>   
      {{a.PSC}} 
    </td>  
    </tr>
  </tbody>
</table>
<form>
      <div class="form-row">
        <div class="col-md-4 mb-3">
          <label for="validationDefault01">Jméno</label>
          <input type="text" class="form-control" id="validationDefault01" placeholder="Jméno" value="Jan" required>
        </div>
        <div class="col-md-4 mb-3">
          <label for="validationDefault02">Příjmení</label>
          <input type="text" class="form-control" id="validationDefault02" placeholder="Příjmení" value="Novak" required>
        </div>
      </div>

      <div class="form-row">
        <div class="col-md-4 mb-3">
          <label for="validationDefault04">Telefon</label>
          <input type="text" class="form-control" id="validationDefault04" placeholder="Telefon" value="777777777" required>
        </div>
      <div class="col-md-4 mb-3">
          <label for="validationDefaultEmail">E-mail</label>
          <div class="input-group">
            <div class="input-group-prepend">
              <span class="input-group-text" id="inputGroupPrepend2">@</span>
            </div>
            <input type="text" class="form-control" id="validationDefaultEmail" placeholder="jan.novak@email.com" aria-describedby="inputGroupPrepend2" required>
          </div>
        </div>
      </div>
      <div class="form-row">
        <div class="col-md-3 mb-3">
          <label for="validationDefault05">Ulice</label>
          <input type="text" class="form-control" id="validationDefault05" placeholder="Ulice" required>
        </div>
        <div class="col-md-3 mb-3">
          <label for="validationDefault06">Město</label>
          <input type="text" class="form-control" id="validationDefault06" placeholder="Město" required>
        </div>
        <div class="col-md-2 mb-3">
          <label for="validationDefault07">PSČ</label>
          <input type="text" class="form-control" id="validationDefault07" placeholder="PSČ" required>
        </div>
      </div>
      <button class="btn btn-primary" type="submit">Uložit záznam</button>
    </form>
  </div>
</template>

<script>
const axios = require("axios")
export default {
  name: 'app',
  data () {
    return {
      zaznamy: []
    }
  },
  methods:{dejdata(){
          axios({
            method:"get", //data z mongos databaze
            url:"http://127.0.0.1:3000",
          }).then(response => {
            this.zaznamy = response.data;
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