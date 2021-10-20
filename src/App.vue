<template>
  <div id="app">

    Kilometers : <input type = "text" v-model = "kilometers">
    Meters : <input type = "text" v-model = "meters">

    <br><br>

    Name : <input type = "text" v-model = "name">
    <p>The name is: {{ this.name }}</p>
    <Alert />
    <Modal />
    <SweetAlert />

<!--    <SkatModal-->
<!--      :modal="{-->
<!--        id: 'custom_modal',-->
<!--        text: 'Custom text to SKAT modal'-->
<!--      }"-->

<!--      :accept="{-->
<!--        class: 'ikon-gem',-->
<!--        id: 'rettelserModal_Savebutton',-->
<!--        text: 'Gem'-->
<!--      }"-->

<!--      :cancel="{-->
<!--        class: 'ikon-arrow-left',-->
<!--        id: 'rettelserModal_Cancelbutton',-->
<!--        text: 'Annuller'-->
<!--      }"-->

<!--      :input="{-->
<!--          enabled: true,-->
<!--          id: 'rettelserModal_incidentNumber',-->
<!--          placeholder: 'This is a placeholder',-->
<!--          required: true,-->
<!--        }"-->

<!--    />-->
    <SkatModal
        :modal="{
        id: 'custom_modal',
        text: 'Hov, der skete en fejl. Prøv igen.'
      }"

        :accept="{
        class: 'ikon-gem',
        id: 'rettelserModal_Savebutton',
        text: 'Luk'
      }"

        :cancel="{
          class: 'ikon-arrow-left',
          id: 'rettelserModal_Cancelbutton',
          text: ''
        }"
    />
  </div>
</template>

<script>

//import { watchEffect } from 'vue'
import Alert from './components/Alert'
import Modal from './components/Modal'
import SweetAlert from "@/components/SweetAlert";
import SkatModal from "@/components/SkatModal";

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
    Modal,
    SweetAlert,
    SkatModal
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
  mounted: function () {
      alert('activated.....')
    this.$bvModal.show('custom_modal')
  }
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
