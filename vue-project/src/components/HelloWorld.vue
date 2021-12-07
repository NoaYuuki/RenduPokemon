<template>
  <div>
    <h1 id="idh1"> Bienvenue dans l'univers Pokemon </h1>
    <img id="id2" src="../assets/pokemon-img.jpg" width="500" hight="auto">
<br>
    <button v-on:click="clicked">Clique </button>
    <button v-on:click="hide">Cache</button>
    <button id="show" v-on:click="show">Montre</button><br>
    <br>
    <p> Bienvenue dans l'exercice de recherche</p>
    <label for="site-search">Trouve ton pokemon:</label>
<input type="number" id="site-search" name="q"
       aria-label="Search through site content">
       <div id='create'></div>
    <div>{{this.url}}</div>
    <img id="src">
    
<button v-on:click="Search">Search</button>
    <p>{{this.info}}</p>
    

  </div>
</template>

<script>
import axios from "axios"

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      info: null,
      name: null,
      url: null,
    };
  },
  methods: {
    clicked: function () {
      console.log("click")
    },
    hide: function () {
      console.log("hide")
      document.getElementById("idh1").style.display = 'none';
    },
    show: function () {
      console.log("show")
      document.getElementById("idh1").style.display = 'block';
    },
    Search: function () {
      console.log("search")
      var url = document.getElementById("site-search").value
      axios
   .get("https://pokeapi.co/api/v2/pokemon/"+ url)
   .then(response => {
     this.info = response.data.name
   })
      }

  },
 mounted (){
   /*axios
   .get("https://pokeapi.co/api/v2/pokemon/")
   .then(response => (this.info = response.data.name))*/
  }

 }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
h1 {
  font-weight: normal;
  background-color:darkslateblue;
  color: white;
  padding: 15px;
  border-radius: 20px;
  margin: 20px 300px;
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
  color: #94ccf1;
}
body{
  background-color:slategray;
  display:inline;
}
p{
  color:white;
}
button{
  background-color:darkslateblue;
  color: white;
  border-radius: 5px;
  padding: 5px 15px;
}
#show{
  background-color:slategray;
  border-color: darkslateblue ;
  color: rgb(255, 255, 255);
}
input{
  padding: 5px;
  border-radius: 3px;
}
img{
  padding: 10px;
}
</style>

