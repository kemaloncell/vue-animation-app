<template>
  <div class="game-area">
    <p>{{ this.answer }}</p>
    <h1 class="title"><span>Where is the</span> Cat?</h1>
    <h4 class="description">After choosing one of the open cards, click on the closed card.</h4>
    <div class="container">
      <transition-group name="rotate-all" class="card-container" appear>
        <app-card :class="{ shadow: selectedCard == card.id }" @click.native="selectedCard = card.id" v-for="card in cards" :card="card" :key="card.id"></app-card>
      </transition-group>
    </div>
    <div class="container">
      <transition name="rotate" mode="out-in">
        <component :card="answer" @click.native="showCard(answer)" :is="activeCard"> </component>
      </transition>
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
      answer: {},
      activeCard: "app-default-card",
      cards: [
        { id: 1, component: "app-card", image: "src/assets/card-1.jpg" },
        { id: 2, component: "app-card", image: "src/assets/card-2.jpg" },
        { id: 3, component: "app-card", image: "src/assets/card-3.jpg" },
        { id: 4, component: "app-card", image: "src/assets/card-4.jpg" },
        { id: 5, component: "app-card", image: "src/assets/card-5.jpg" },
      ],
    };
  },
  created() {
    let answer = Math.ceil(Math.random() * this.cards.length);
    // 1-5
    this.answer = this.cards[answer - 1];
  },
  methods: {
    showCard(answer) {
      if (this.selectedCard == null) {
        alert("Please select a card!!");
      } else {
        setTimeout(() => {
          this.activeCard = answer.component;
          if (answer.id == this.selectedCard) {
            // alert("d");
            this.$emit("isCorrectEvent", "app-celebrate");
          } else {
            alert("y");
            this.$emit("isCorrectEvent", "app-failure");
          }
        }, 1000);
      }
    },
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

.container,
.card-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 50px;
}

.shadow {
  box-shadow: 0px 5px 48px #30969f !important;
  transition: box-shadow 0.5s;
}

/* Animation for cards */
.rotate-all-enter {
}
.rotate-all-enter-active {
  animation: rotate-all ease-in-out 2s forwards;
}
.rotate-all-leave {
}
.rotate-all-leave-active {
  animation: rotate-all ease-in-out 2s forwards;
}

@keyframes rotate-all {
  from {
    transform: rotateY(0);
  }
  to {
    transform: rotateY(1080deg);
  }
}

/* Animation for card */
.rotate-enter {
}
.rotate-enter-active {
  animation: rotate-in 0.5s ease-in-out forwards;
}
.rotate-leave {
}
.rotate-leave-active {
  animation: rotate-out 0.5s ease-in-out forwards;
}
@keyframes rotate-in {
  from {
    transform: rotateY(90deg);
  }
  to {
    transform: rotateY(0deg);
  }
}
@keyframes rotate-out {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(90deg);
  }
}
</style>
