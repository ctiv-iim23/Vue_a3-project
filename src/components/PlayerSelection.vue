<template>
  <div class="border border-black text-center m-4 p-4 font-bold">
    Ma sélection de joueurs : {{ selection.length }}
    <span v-if="nbrPlayers">joueurs</span>
    <span v-else>joueur</span>

    <ul>
      <li v-for="joueur in selection" :key="joueur.name">{{ joueur.name }}</li>
    </ul>
  </div>
  <div class="m-4 p-4">
    <img :src="require('../assets/img/logo.png')" />
  </div>
</template>

<script>
export default {
  name: "player-selection",
  props: ["selection"],
  computed: {
    nbrPlayers() {
      if (this.selection.length > 1) {
        return true;
      }
      return false;
    },
  },
};
</script>

<style></style>
