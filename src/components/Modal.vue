<template>
  <div>
    <b-button v-b-modal.modal-1>Launch demo modal, but is set to open automatically</b-button>

    <b-modal ref="my-modal" id="modal-1" title="BootstrapVue">
      <p class="my-4">Hello from modal!</p>
    </b-modal>
  </div>
</template>

<script>
export default {
  name: "Modal",
  data() {
    return {
      theValue: 1,
    }
  },
  methods: {
    showModal() {
      this.$refs['my-modal'].show()
    }
  },
  mounted: function (){
    if (this.theValue !== 2){
      this.showModal()
    }
  }

}
</script>

<style scoped>

</style>
