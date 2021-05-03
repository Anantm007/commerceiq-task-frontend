<template>
  <div class="chat-body" id="scrollDivId">
    <div class="chats">
      <ChatMessages :allMessages="allMessages" />
    </div>
  </div>
</template>

<script>
import ChatMessages from "./ChatMessages";

export default {
  name: "ChatBody",

  // Child component to display
  components: {
    ChatMessages,
  },

  // Props received from the parent
  props: {
    allMessages: Array,
  },
};
</script>

<style scoped>
.chat-body {
  overflow-y: scroll;
  border-radius: 4px;
  height: 15rem !important;
}

/*Custom scrollbar to make it visible on mobile devices*/
::-webkit-scrollbar {
  -webkit-appearance: none;
  width: 0.5rem;
}

::-webkit-scrollbar-thumb {
  border-radius: 0px;
  background-color: #cdc7be;
  box-shadow: 0 0 1px rgba(255, 255, 255, 0.5);
}

.chats {
  padding: 1rem 0.98rem;
  background: #fff;
}
</style>
