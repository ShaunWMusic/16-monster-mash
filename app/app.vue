<template lang="html">
<div class="app">
<div class="sidebar">
  <div class="sidebar-header">
    <h1>Build Your Monster</h1>
  </div>
</div>



</div>
</template>

<script>
import Vue from 'vue';


export default Vue.extend {
  data() {
  return {
  };
},

  mounted() {

  },

  methods: {
    changeBodyShape() {

    },
    nextBody() {

    },
    previousBody() {

    },
    changeMouthShape() {

    },
    nextMouth() {

    },
    previousMouth() {

    },
    changeEyeShape() {

    },
    nextEyes() {

    },
    previousEyes() {

    },

    saveFavorites() {


      this.form = {
      author: '',
      body: '',
    };
    },

  }

}
</script>

<style lang="css">
  .sidebar-header {
    background: black;
    color: white;
  }
</style>
