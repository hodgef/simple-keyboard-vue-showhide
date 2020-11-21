<template>
  <div id="app">
    <input
      :value="input"
      class="input"
      @click="isKeyboardOpen = true"
      @input="onInputChange"
      placeholder="Type then hit enter on simple-keyboard to hide"
    >
    <SimpleKeyboard
      v-if="isKeyboardOpen"
      @onChange="onChange"
      @onKeyPress="onKeyPress"
      :input="input"
    />
  </div>
</template>

<script>
import SimpleKeyboard from "./SimpleKeyboard";
import "./App.css";

export default {
  name: "App",
  components: {
    SimpleKeyboard
  },
  data: () => ({
    input: "",
    isKeyboardOpen: false
  }),
  methods: {
    onChange(input) {
      this.input = input;
    },
    onKeyPress(button) {
      if (button === "{enter}") {
        this.isKeyboardOpen = false;
      }
    },
    onInputChange(input) {
      this.input = input.target.value;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
