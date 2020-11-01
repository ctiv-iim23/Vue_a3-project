<template>
  <div class="flex">
    <div class="w-1/5">
      <player-selection :selection="selection"> </player-selection>
    </div>

    <div class="w-4/5 mt-2">
      <player-card
        v-for="(player, index) in playersData.players"
        :key="index"
        :player="player"
        @add-player="addPlayerToSelection"
      >
      </player-card>
    </div>
  </div>
</template>

<script>
import playersData from "../assets/data/players.json";
import playerCard from "./PlayerCard.vue";
import playerSelection from "./PlayerSelection.vue";

export default {
  name: "player-List",
  components: {
    playerCard,
    playerSelection,
  },
  data() {
    return {
      playersData: playersData,
      selection: [],
    };
  },
  methods: {
    addPlayerToSelection(player) {
      this.selection.push(player);
      this.$emit("child-event", player);
    },
  },
};
</script>

<style></style>
