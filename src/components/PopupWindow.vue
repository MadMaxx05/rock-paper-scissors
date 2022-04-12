<template>
  <div class="window-container">
    <div class="window">
      <h2>{{ winner }}</h2>
      <p>Player: {{ playerMove }}</p>
      <p>Computer: {{ computerMove }}</p>
      <button @click="onClick()" class="btn">Play Again!</button>
    </div>
    <div class="overlay"></div>
  </div>
</template>

<script>
export default {
  name: "PopupWindow",
  props: {
    winner: String,
    playerMove: String,
    computerMove: String,
  },
  methods: {
    onClick() {
      this.$emit("close-window");
    },
  },
};
</script>

<style lang="scss" scoped>
.overlay {
  position: fixed;
  inset: 0;
  z-index: -1;
  background-color: rgba(0, 0, 0, 0.3);
}

.window-container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.window {
  padding: 35px 0;
  margin: 0;
  border-radius: 12px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  background-color: #fff;
  width: 90%;
  max-width: 600px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;

  h2 {
    margin-bottom: 17px;
  }

  p {
    margin-bottom: 4px;
  }

  .btn {
    margin-top: 35px;
    border: none;
    border-radius: 15px;
    background-color: rgb(108, 212, 152);
    color: #000;
    padding: 17px 25px;
    cursor: pointer;
    font-size: 14px;
    text-transform: uppercase;
    font-weight: 700;
    transition: 0.2s;

    &:hover {
      background-color: rgb(97, 189, 135);
    }
  }
}
</style>
