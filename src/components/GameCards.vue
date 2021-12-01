<template>
  <div class="game-area">
    <h1 class="title"><span>Where is the</span> Cat?</h1>
    <h4 class="description">After choosing one of the open cards, click on the closed card.</h4>
    <div class="container">
      <app-card v-for="i in 5" :key="i"></app-card>
    </div>
    <div class="container"></div>
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
  components: {
    appCard: Card,
  },
};
</script>

<style scoped>
.title {
  text-align: center;
  color: rosybrown;
}
.title span {
  color: mediumpurple;
}

.description {
  color: grey;
  text-align: center;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 50px;
}
</style>
