<template>
  <nav-bar @change-component="updateSelectedComponent"></nav-bar>
  <keep-alive include="player-list">
    <component
      :is="selectedComponent"
      v-bind="currentProps"
      @child-event="selectionUpdate"
    >
    </component>
  </keep-alive>
</template>

<script>
import PlayerList from "./components/PlayerList.vue";
import SelectionList from "./components/SelectionList.vue";
import NavBar from "./components/navigation/NavBar.vue";

export default {
  name: "App",
  components: {
    PlayerList,
    NavBar,
    SelectionList,
  },
  data() {
    return {
      selectedComponent: "player-list",
      playerSelect: [],
    };
  },
  computed: {
    currentProps() {
      if (this.selectedComponent == "selection-list") {
        return { selection: this.playerSelect };
      }
      return false;
    },
  },
  methods: {
    updateSelectedComponent(value) {
      this.selectedComponent = value;
    },
    selectionUpdate(value) {
      this.playerSelect.push(value);
    },
  },
};
</script>
