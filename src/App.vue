<template>
  <components @isCorrectEvent="activeComponent = $event" :is="activeComponent"></components>
</template>
<script>
import GameCards from "./components/GameCards.vue";
import Failure from "./components/Failure.vue";
import Celebrate from "./components/Celebrate.vue";
export default {
  components: {
    appGameCards: GameCards,
    appFailure: Failure,
    appCelebrate: Celebrate,
  },
  data() {
    return {
      activeComponent: "app-game-cards",
    };
  },
};
</script>
<style>
body {
  font-family: sans-serif;
}
</style>
