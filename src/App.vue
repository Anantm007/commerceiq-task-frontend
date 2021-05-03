<template>
  <div class="container">
    <AppHeading />
    <div v-if="show" class="outer-div">
      <ChatWindow />
    </div>
    <ShowChat @toggle-show-chat="handleSwitch" />
  </div>
</template>

<script>
// Import component to render
import AppHeading from "./components/AppHeading";
import ChatWindow from "./components/ChatWindow";
import ShowChat from "./components/ShowChat";

export default {
  // Name of the component
  name: "App",

  // The component to render
  components: { AppHeading, ChatWindow, ShowChat },

  // State to hide/unhide the app
  data() {
    return {
      show: true,
    };
  },

  // Component methods
  methods: {
    // Handle opening and closing of the chat window
    handleSwitch() {
      this.show = !this.show;
    },
  },
};
</script>

<style>
body {
  background-color: #f0e3ca;
}

.outer-div {
  margin-bottom: 0.5rem;
  margin-right: -1rem;
  width: 25rem;
  height: 30rem;
  position: absolute;
  bottom: 0;
  right: 0;
}
</style>
