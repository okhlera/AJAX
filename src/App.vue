<template>
  <div id="app">
    <user-card v-if="user" :user="user"></user-card>
      <button v-on=getUserData>click me</button>

  </div>
</template>

<script>
import UserCard from './components/UserCard'
export default {
  data(){
    return {
      user: null
    }
  },
  name: 'app',
  components: {
    UserCard
  },
  mounted(){
    this.axios.get('https://randomuser.me/api').then((response)=>{
      console.log('response', response.data)
      this.user = response.data.results[0]
    }).catch(err=>{
      console.log('errr', err)
    })

  },
  methods:{
    getUserData: function(){
      this.axios.get('https://randomuser.me/api').then((response)=>{
      console.log('response', response.data)
      this.user = response.data.results[0]
    }).catch(err=>{
      console.log('errr', err)
    })

    }
  }
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
</style>
