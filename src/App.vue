<template>
  <div id="app">
    <ul>
      <li v-show="mailingList.length == 10" v-for="el in mailingList" :key="el">{{el}}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  components: {

  },

  data: function(){
    return{
      mailingList: []

    }
  },
  mounted: function(){
    for(let i = 0; i < 10; i++){
      axios.get('https://flynn.boolean.careers/exercises/api/random/mail').then(res => {
      this.mailingList.push(res.data.response)});
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
