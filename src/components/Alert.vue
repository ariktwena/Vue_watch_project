<template>
  <div>
    <p>The alert</p>
<!--    {{ this.runAlertCustom()}}$-->
<!--    {{ this.runAlertDefault() }}-->
    {{ alert1 }}
  </div>
</template>

<script>

import * as alerts from '../functions'

export default {
  name: "alert",
  data() {
    return {
      input: 'This is an custom alert!!',
    }
  },
  props: {
    alert1: alerts.alertBoxDefault()
  },
  methods: {
    runAlertCustom() {
      alerts.alertBoxDefault(this.input)
    },
    runAlertDefault(){
      alerts.alertBoxDefault()
    }
  }

}
</script>

<style scoped>

</style>
