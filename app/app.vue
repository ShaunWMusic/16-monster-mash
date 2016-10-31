<template lang="html">
<div class="app">
<div class="sidebar">
  <div class="sidebar-header">
    <h1>Build Your Monster</h1>
  </div>
  <div class="body-img-switcher img-switcher">
  <button class="btn" @click="updatePart('body', -1)"><span class="fa fa-angle-left"></span></button>
  <div class="frame">
    <img :src="'/monsters/' + monsterParts.body[selected.body] + '.png'" alt="" />
  </div>
  <button class="btn" @click="updatePart('body', 1)"><span class="fa fa-angle-right"></span></button>
</div>
  <div class="mouth-img-switcher img-switcher">
  <button class="btn" @click="updatePart('mouth', -1)"><span class="fa fa-angle-left"></span></button>
  <div class="frame">
    <img :src="'/monsters/' + monsterParts.mouth[selected.mouth] + '.png'" alt="" />
  </div>
  <button class="btn" @click="updatePart('mouth', 1)"><span class="fa fa-angle-right"></span></button>
</div>
  <div class="eyes-img-switcher img-switcher">
  <button class="btn" @click="updatePart('eyes', -1)"><span class="fa fa-angle-left"></span></button>
  <div class="frame">
    <img :src="'/monsters/' + monsterParts.eyes[selected.eyes] + '.png'" alt="" />
  </div>
  <button class="btn" @click="updatePart('eyes', 1)"><span class="fa fa-angle-right"></span></button>
</div>
<form>
      <input type="type" placeholder="NAME YOUR CREATION" name="name">
      <button>Save Favorite</button>
      </form>
</div>
<div class="main">
<div class="grid">
  <div class="grid-item">
    <div class="monster">
      <img :src="'/monsters/' + monsterParts.body[selected.body] + '.full.png'" alt="" />
      <img :src="'/monsters/' + monsterParts.eyes[selected.eyes] + '.full.png'" alt="" />
      <img :src="'/monsters/' + monsterParts.mouth[selected.mouth] + '.full.png'" alt="" />
    </div>
  </div>
</div>
</div>



</div>
</template>

<script>
import Vue from 'vue';
import monsterParts from './monster-parts';

export default Vue.extend({
  data() {
    return {
      selected: {
        body: 0,
        eyes: 0,
        mouth: 0,
      },
      monsterParts,
    };
  },

  mounted() {

  },

  methods: {
    updatePart(partName, difference = 1) {
      this.selected[partName] = (this.selected[partName] + difference) % this.monsterParts[partName].length;
    }
  }

})
</script>
