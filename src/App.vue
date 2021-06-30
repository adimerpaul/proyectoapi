<template>
  <div id="app">
<!--    <img alt="Vue logo" src="./assets/logo.png">-->
<!--    <HelloWorld msg="Hola vue"/>-->
<!--    <ul>-->
<!--      <li v-for="(pokemon,index) in pokemons" :key="index">-->
<!--      {{pokemon.name}}-->
<!--      </li>-->
<!--    </ul>-->
    <div class="container">
      <div class="row">

        <div v-for="(pokemon,index) in pokemons" :key="index" class="col-2">
          <div class="card">
            <img v-bind:src="'https://pokeres.bastionbot.org/images/pokemon/'+parseInt(index+1)+'.png'" class="card-img-top" >
            <div class="card-body">
              <p class="card-text">
                {{pokemon.name}}
              </p>
            </div>
          </div>
        </div>

      </div>
    </div>

  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
  },
  data(){
    return {
      pokemons:[],
    }
  },
  created() {
    this.axios.get('https://pokeapi.co/api/v2/pokemon?limit=151&offset=0').then(res=>{
      // console.log(res.data)
      this.pokemons=res.data.results;
    })
  }
}
</script>

