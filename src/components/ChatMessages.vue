<template>
  <!-- Loop through all the messages and use "if" directive to render 
  either the admin message(s) or 
  user message(s)-->
  <div v-for="message in allMessages" :key="message.id">
    <div v-if="message.owner === 'admin'">
      <ChatMessageAdmin :message="message" />
    </div>
    <div v-if="message.owner === 'user'">
      <ChatMessageUser :message="message" />
    </div>
  </div>
</template>

<script>
// Import component to render
import ChatMessageAdmin from "./ChatMessageAdmin";
import ChatMessageUser from "./ChatMessageUser";

export default {
  // Name of the component
  name: "ChatMessages",

  // Child components to render
  components: { ChatMessageAdmin, ChatMessageUser },

  // Props received from the parent
  props: {
    allMessages: Array,
  },
};
</script>
