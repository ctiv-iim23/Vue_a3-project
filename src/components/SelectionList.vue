<template>
  <div class="container w-4/5 mx-auto mt-4">
    <h1 class="text-lg font-bold">Joueurs Sélectionnés</h1>

    <div v-if="selection.length == 1">
      <div
        v-for="player in selection"
        :key="player.name"
        class="border border-black my-4 p-2"
      >
        <h3>{{ player.name }} ({{ player.number }})</h3>
        <span>Né le {{ player.birthDate }}</span>
      </div>
    </div>
    <div v-else>
      <p>Vous n'avez pas selectionné de joueurs</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "selection-list",
  props: ["selection"],
};
</script>

<style></style>
