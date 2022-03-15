<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <router-view/>
    <button @click="show = !show">Sign In</button> |
    <button v-if="!show">Sign Out</button>

    <div>
    <div class="container" v-for="card in cards" :key="card.id">
      <h1>{{card.title}}</h1>
      <p>{{card.content}}</p>
    </div>
    </div>
    
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>

<script>
export default {
  data() {
    return {
      show: true, 
      cards:[]
    }
  },
  methods: {
    async getInfo() {
     const info = await fetch ("http://localhost:3000/cards");
     const cardsInfo = await info.json();
     this.card = cardsInfo;
     console.log(cardsInfo)
    }
  }
}
</script>

