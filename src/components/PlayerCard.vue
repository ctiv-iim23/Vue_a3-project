<template>
  <div
    class="border border-green-900 m-2 p-2 rounded bg-gray-300"
    :class="isInjuredClass"
  >
    <div>
      <h3 class="text-lg font-bold">{{ playerName }} ({{ player.number }})</h3>
      <p>{{ player.position }}</p>
    </div>
    <base-button text="Sélectionner" @click="addToSelection"></base-button>
  </div>
</template>

<script>
export default {
  name: "player-card",
  props: ["player"],
  computed: {
    playerName() {
      if (this.player.name.split(".").length > 1) {
        return this.player.name.split(".")[1];
      }
      return this.player.name;
    },
    playerInjured() {
      if (this.player.health == "out") {
        return true;
      }
      return false;
    },
    isInjuredClass() {
      return {
        "bg-red-500": this.playerInjured,
        "bg-green-500": !this.playerInjured,
      };
    },
  },
  methods: {
    addToSelection() {
      this.$emit("add-player", this.player);
    },
  },
};
</script>

<style scoped></style>
