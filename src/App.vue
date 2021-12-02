<template>
  <transition name="slideContainer" mode="out-in">
    <components @activeComponentEvent="activeComponent = $event" :is="activeComponent"></components>
  </transition>
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
/*I don't need to use these tags again since I have specified the beginning and the end in keyframes.*/
.slideContainer-enter {
}
.slideContainer-enter-active {
  animation: slide-in 0.3s ease-in-out forwards;
}
.slideContainer-leave {
}
.slideContainer-leave-active {
  animation: slide-out 0.3s ease-in-out forwards;
}

@keyframes slide-in {
  from {
    transform: translateX(-1000px);
    opacity: 0;
  }
  to {
    transform: translateX(0px);
    opacity: 1;
  }
}

@keyframes slide-out {
  from {
    transform: translateX(0px);
    opacity: 0;
  }
  to {
    transform: translateX(1000px);
    opacity: 1;
  }
}
</style>
