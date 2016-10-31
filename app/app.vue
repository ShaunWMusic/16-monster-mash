<template lang="html">
<div class="app">
<div class="sidebar">
  <div class="sidebar-header">
    <h1>Build Your Monster</h1>
  </div>
  <div class="body-img-switcher">
  <button class="btn" @click="nextBody()">Back</button>
  <div class="frame">
    <img :src="apod.url" :alt="apod.title" />
  </div>
  <button class="btn" @click="previousBody()">Forward</button>
</div>
<form @submit.prevent="saveFavorites(form.author, form.body)">
      <input type="type"  name="name" v-model="form.author">
      <textarea rows="8" cols="40" v-model="form.body"></textarea>
      <button>Submit</button>
      </form>
</div>



</div>
</template>

<script>
import Vue from 'vue';

export default Vue.extend({
  data() {
  return {
  };
},

  mounted() {

  },

  methods: {

  }

})
</script>
