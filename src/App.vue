<template>
  <div id="app">

    Kilometers : <input type = "text" v-model = "kilometers">
    Meters : <input type = "text" v-model = "meters">

    <br><br>

    Name : <input type = "text" v-model = "name">
    <p>The name is: {{ this.name }}</p>
    <Alert />
    <Modal />
  </div>
</template>

<script>

//import { watchEffect } from 'vue'
import Alert from './components/Alert'
import Modal from './components/Modal'

export default {
  name: 'App',
  data() {
    return {
      kilometers: 0,
      meters: 0,
      name: ''
    }
  },
  methods: {
  },
  computed :{
  },
  components: {
    Alert,
    Modal
  },
  watch : {
    kilometers:function(val) {
      this.kilometers = val;
      this.meters = val * 1000;
    },
    meters : function (val) {
      this.kilometers = val/ 1000;
      this.meters = val;
      console.log('hallo')
    },
    name : function (val) {
      console.log('We do something with: ', val)
    }
  },
  //watchEffect(() => console.log("Name: " + this.name))
}
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
