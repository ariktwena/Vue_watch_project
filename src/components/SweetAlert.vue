<!--yarn add sweetalert-->
<!--https://github.com/t4t5/sweetalert-->
<!--https://yarnpkg.com/package/sweetalert-->

<template>
  <div>
    <h1>Sweet Alert</h1>
    <button @click="showSweetAlert_1()">Open Sweet Alert 1</button>
    {{this.showSweetAlert_1()}}
    <button @click="showSweetAlert_2()">Open Sweet Alert 2</button>
    <button @click="showSweetAlert_3()">Open Sweet Alert 3</button>
  </div>
</template>

<script>
import swal from 'sweetalert';

export default {
  name: "SweetAlert",
  data () {
    return {
      value: 2
    }
  },
  methods: {
    showSweetAlert_1 (){
      swal("Hello world!");
    },
    showSweetAlert_2 (){
      swal("Oops!", "Something went wrong!", "error");
    }
    ,
    showSweetAlert_3 (){
      swal({
        title: "Are you sure?",
        text: "Are you sure that you want to leave this page?",
        icon: "warning",
        dangerMode: true,
      })
          .then(willDelete => {
            if (willDelete) {
              swal("Deleted!", "Your imaginary file has been deleted!", "success");
            }
          });
    }
  }
}
</script>

<style scoped>

</style>
