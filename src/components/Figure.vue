<template>
  <div class="container">
    <button @click="onClick(name)" class="icon-border">
      <i :class="icon"></i>
    </button>
    <h2>{{ name }}</h2>
  </div>
</template>

<script>
export default {
  name: "Figure",
  props: {
    name: String,
    icon: String,
  },
  methods: {
    onClick(name) {
      this.$emit("player-move", name);
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100px;
  margin: 0 5px;
}

.icon-border {
  box-sizing: content-box;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 60px;
  height: 60px;

  padding: 15px;
  background-color: white;
  border: none;
  border-radius: 50%;
  cursor: pointer;
  transition: 0.1s;
  box-shadow: 0px 2px 3px 1px rgba(0, 0, 0, 0.2);
  -webkit-tap-highlight-color: transparent;

  &:hover {
    box-shadow: 0px 4px 6px 3px rgba(0, 0, 0, 0.2);
  }

  &:active {
    box-shadow: 0px 4px 6px 3px rgba(0, 0, 0, 0.2);
    background-color: rgb(59, 59, 59);
  }

  i {
    color: rgb(59, 59, 59);
    font-size: 60px;
    transition: 0.1s;
    flex: 0 0 60px;

    &:active {
      color: #fff;
    }
  }
}

h2 {
  margin-top: 15px;
  font-size: 25px;
  color: #fff;
  font-weight: 400;
}
</style>
