<template>
  <div class="game-area">
    <h1 class="title"><span>Where is the</span> Cat?</h1>
    <h4 class="description">After choosing one of the open cards, click on the closed card.</h4>
    <div class="container">
      <app-card :class="{ shadow: selectedCard == card.id }" @click.native="selectedCard = card.id" v-for="card in cards" :card="card" :key="card"></app-card>
    </div>
    <div class="container">
      <app-default-card></app-default-card>
    </div>
  </div>
</template>

<script>
import Card from "./Card.vue";
import DefaultCard from "./DefaultCard.vue";
export default {
  components: {
    appCard: Card,
    appDefaultCard: DefaultCard,
  },
  data() {
    return {
      selectedCard: null,
      cards: [
        { id: 1, component: "app-cards", image: "src/assets/card-1.jpg" },
        { id: 2, component: "app-cards", image: "src/assets/card-2.jpg" },
        { id: 3, component: "app-cards", image: "src/assets/card-3.jpg" },
        { id: 4, component: "app-cards", image: "src/assets/card-4.jpg" },
        { id: 5, component: "app-cards", image: "src/assets/card-5.jpg" },
      ],
    };
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

.shadow {
  box-shadow: 0px 5px 48px #30969f !important;
  transition: box-shadow 0.5s;
}
</style>
