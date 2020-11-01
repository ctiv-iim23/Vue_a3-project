<template>
  <div class="container w-4/5 mx-auto mt-4">
    <h1 class="text-lg font-bold">Joueurs Sélectionnés</h1>

    <div v-if="selection.length == 0">
      <p>
        Vous n'avez pas selectionné de joueurs. :( <br />
        Allez sur "Tous les joueurs" puis sélectionnez-les ! ;)
      </p>
    </div>
    <div v-else>
      <span>Total : {{ total }}</span>
      <div
        v-for="player in selection"
        :key="player.name"
        class="border border-black my-4 p-2 "
      >
        <h3 class="text-lg font-bold">
          ({{ player.number }}) {{ player.name }}
          <span>| {{ player.country }}</span>
        </h3>
        <span class="italic">Né le {{ player.birthDate }}</span
        ><br />
        <h2 class="font-bold">
          <span>Poste : {{ player.position }}</span>
        </h2>
        <img :src="playerPhoto(player.photo)" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "selection-list",
  props: ["selection"],
  methods: {
    playerPhoto(img) {
      return require("@/assets/img/" + img);
    },
  },
  computed: {
    total() {
      if (this.selection.length > 1) {
        return this.true;
      }
      return this.total;
    },
  },
};
</script>

<style></style>
