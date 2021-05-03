<template>
  <div class="container col-md-12 col-xs-12 col-md-offset-2">
    <!-- The heading of the chat window -->
    <ChatHeader />

    <!-- Chat body, where all the messages are displayed -->
    <ChatBody :allMessages="allMessages" />

    <!-- Add a new message form -->
    <SendMessage @add-message="addMessage" />
  </div>
</template>

<script>
// Components to render
import ChatHeader from "./ChatHeader";
import ChatBody from "./ChatBody";
import SendMessage from "./SendMessage";

// Base URL to make request to the server
const BASE_URL = "https://commerce-task.anantmathur.me/api";

export default {
  // Name of the component
  name: "ChatWindow",

  // Child components to render here
  components: {
    ChatHeader,
    ChatBody,
    SendMessage,
  },

  /* State of this component
   * adminMessages: That will be displayed from the left side (chat bot)
   * userMessages: Messages submitted by user, will be displayed from right side (user)
   * allMessages: Combination of the above 2 along with the "owner" filed to segregate them while rendering
   */
  data() {
    return {
      adminMessages: [],
      userMessages: [],
      allMessages: [],
    };
  },

  methods: {
    /* Add a new message to the DB
     * @params: message - text message to store
     */
    async addMessage(message) {
      // Message object tailored according to the backend
      const msg = {
        id: Math.floor(Math.random() * 100000),
        text: message,
        timestamp: new Date(),
      };

      // Make a request to the backend, with the body and headers
      const res = await fetch(`${BASE_URL}/messages`, {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(msg),
      });

      // Convert response to json
      const data = await res.json();

      // The backend returns all the messages (including the new one)
      const messages = data.data;

      // adminMessages state is updated to have this new message
      this.adminMessages = data.data;

      // userMessages will now also include the message we sent
      this.userMessages = [...this.userMessages, msg];

      // The allMessages array will contain this object but with the user as owner (to help in segregation)
      this.allMessages.push({ ...msg, owner: "user" });

      // Add owner property (as admin) to these messages and push into the allMessages array
      data.data.map((msg) => {
        msg["owner"] = "admin";
        this.allMessages.push(msg);
      });
    },
  },

  // Lifecycle method invoked when the component renders
  async created() {
    // Fetch all the existing messages from the server
    const res = await fetch(`${BASE_URL}/messages`);

    // Convert response to JSON
    const data = await res.json();

    // the adminMessages will have all the pre existing messages we just fetched
    this.adminMessages = data.data;

    // A custom first message whenever the user lands on the application
    const firstMsg = {
      id: 0,
      text:
        "WELCOME TO THE CHAT APP, YOU CAN ADD A NEW MESSAGE BY TYPING IN THE BOX BELOW. ALL MESSAGES WILL BE DISPLAYED BELOW!",
      timestamp: new Date(),
    };

    // Add the fist message on top
    this.adminMessages.unshift(firstMsg);

    // Add the owner property to the messages and push everything into the allMessages array
    this.adminMessages.map((msg) => {
      msg["owner"] = "admin";
      this.allMessages.push(msg);
    });
  },
};
</script>

<style scoped>
.container {
  max-width: 80%;
  margin: 3.5rem auto 3.5rem auto;
  overflow: none;
  border: 1px solid black;
  border-radius: 5px;
  background: #344fa1 !important;
  border: 3px solid black;
}
</style>
