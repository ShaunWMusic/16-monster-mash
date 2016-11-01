<template lang="html">
<div class="app">
<div class="sidebar">
    <h1 class="sidebar-header">Build Your Monster</h1>

  <div class="sidebar__img-switcher">
  <button class="btn" @click="updatePart('body', -1)"><span class="fa fa-angle-left"></span></button>
  <div class="sidebar__frame">
    <img class="sidebar__img" :src="'/monsters/' + monsterParts.body[selected.body] + '.png'" alt="" />
  </div>
  <button class="btn" @click="updatePart('body', 1)"><span class="fa fa-angle-right"></span></button>
</div>
  <div class="sidebar__img-switcher">
  <button class="btn" @click="updatePart('mouth', -1)"><span class="fa fa-angle-left"></span></button>
  <div class="sidebar__frame">
    <img class="sidebar__img" :src="'/monsters/' + monsterParts.mouth[selected.mouth] + '.png'" alt="" />
  </div>
  <button class="btn" @click="updatePart('mouth', 1)"><span class="fa fa-angle-right"></span></button>
</div>
  <div class="sidebar__img-switcher">
  <button class="btn" @click="updatePart('eyes', -1)"><span class="fa fa-angle-left"></span></button>
  <div class="sidebar__frame">
    <img class="sidebar__img" :src="'/monsters/' + monsterParts.eyes[selected.eyes] + '.png'" alt="" />
  </div>
  <button class="btn" @click="updatePart('eyes', 1)"><span class="fa fa-angle-right"></span></button>
</div>
<form @submit.prevent="saveMonster">
      <input type="type" placeholder="NAME YOUR CREATION" name="name" v-model="selected.name">
      <button class="btn-save__favorite">Save Favorite</button>
      </form>
</div>
<div class="app__main">
  <div class="frame">
    <div class="monster">
      <img class="monster__img" :src="'/monsters/' + monsterParts.body[selected.body] + '.full.png'" alt="" />
      <img class="monster__img" :src="'/monsters/' + monsterParts.eyes[selected.eyes] + '.full.png'" alt="" />
      <img class="monster__img" :src="'/monsters/' + monsterParts.mouth[selected.mouth] + '.full.png'" alt="" />
    </div>
  </div>

  <div class="favorite-list">
      <div class="favorite-list__item" v-for="monster in monsters">
        <div class="monster">
          <img class="monster__img" :src="'/monsters/' + monsterParts.body[monster.body] + '.full.png'" alt="" />
          <img class="monster__img" :src="'/monsters/' + monsterParts.eyes[monster.eyes] + '.full.png'" alt="" />
          <img class="monster__img" :src="'/monsters/' + monsterParts.mouth[monster.mouth] + '.full.png'" alt="" />
        </div>
        <h2>{{ monster.name }}</h2>
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
        name: '',
      },
      monsterParts,

      monsters: [],
    };
  },

  created() {
    fetch('http://tiny-tn.herokuapp.com/collections/swm-monsters')
      .then((r) => r.json())
      .then((monsters) => {
        this.monsters = monsters;
      });
  },

  methods: {
    updatePart(partName, difference = 1) {
      this.selected[partName] = (this.selected[partName] + difference + this.monsterParts[partName].length) % this.monsterParts[partName].length;
    },
    saveMonster(monsters) {
      fetch('http://tiny-tn.herokuapp.com/collections/swm-monsters', {
         method: 'POST',
         headers: {
           'Content-Type' : 'application/json'
         },
         body: JSON.stringify(this.selected),
      }).then((r) => r.json())
      .then((data) => {
        this.monsters = [data, ...this.monsters];
      })
    },
  },

});
</script>
