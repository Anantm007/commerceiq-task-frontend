<template>
  <ChatWindow />
</template>

<script>
// Import component to render
import ChatWindow from "./components/ChatWindow";

export default {
  // Name of the component
  name: "App",

  // The component to render
  components: { ChatWindow },
};
</script>

<style>
body {
  background: #e1f1dd;
}
</style>
