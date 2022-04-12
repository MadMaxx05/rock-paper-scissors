<template>
  <div class="home">
    <h1>Choose your figure:</h1>
    <div class="figures">
      <Figure
        @player-move="compareMoves"
        @click="showPopupWindow = true"
        name="Rock"
        icon="fas fa-hand-rock"
      />
      <Figure
        @player-move="compareMoves"
        @click="showPopupWindow = true"
        name="Paper"
        icon="fas fa-hand-paper"
      />
      <Figure
        @player-move="compareMoves"
        @click="showPopupWindow = true"
        name="Scissors"
        icon="fas fa-hand-scissors"
      />
    </div>
  </div>
  <PopupWindow
    v-if="showPopupWindow"
    @close-window="showPopupWindow = false"
    :winner="winner"
    :playerMove="player"
    :computerMove="computer"
  />
</template>

<script>
// @ is an alias to /src

import Figure from "@/components/Figure.vue";
import PopupWindow from "@/components/PopupWindow.vue";

export default {
  name: "App",
  components: {
    Figure,
    PopupWindow,
  },
  data() {
    return {
      showPopupWindow: false,
      winner: "",
      player: "",
      computer: "",
    };
  },
  methods: {
    computerMove() {
      let random = Math.floor(Math.random() * 3);

      switch (random) {
        case 0: {
          //console.log("Computer: Rock");
          this.computer = "Rock";
          return "Rock";
        }
        case 1: {
          //console.log("Computer: Paper");
          this.computer = "Paper";
          return "Paper";
        }
        case 2: {
          //console.log("Computer: Scissors");
          this.computer = "Scissors";
          return "Scissors";
        }
      }
    },
    compareMoves(playerMove) {
      //console.log("Player: " + playerMove);
      this.player = playerMove;
      let computerMove = this.computerMove();

      if (playerMove === "Rock" && computerMove === "Rock") {
        this.winner = "It's a draw!";
      } else if (playerMove === "Rock" && computerMove === "Paper") {
        this.winner = "Computer won!";
      } else if (playerMove === "Rock" && computerMove === "Scissors") {
        this.winner = "Player won!";
      }

      if (playerMove === "Paper" && computerMove === "Paper") {
        this.winner = "It's a draw!";
      } else if (playerMove === "Paper" && computerMove === "Rock") {
        this.winner = "Player won!";
      } else if (playerMove === "Paper" && computerMove === "Scissors") {
        this.winner = "Computer won!";
      }

      if (playerMove === "Scissors" && computerMove === "Scissors") {
        this.winner = "It's a draw!";
      } else if (playerMove === "Scissors" && computerMove === "Rock") {
        this.winner = "Computer won!";
      } else if (playerMove === "Scissors" && computerMove === "Paper") {
        this.winner = "Player won!";
      }
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: "Poppins", sans-serif;
  font-size: 20px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: rgb(255, 196, 0);
  margin: 0;
  padding: 0;
  color: #2c3e50;
  position: relative;
}

.home {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  h1 {
    margin-bottom: 30px;
    color: #fff;
    text-transform: uppercase;
    font-weight: 500;
  }

  .figures {
    display: flex;
    justify-content: space-around;
    align-items: center;
    width: 100%;
    max-width: 500px;
  }
}
</style>
