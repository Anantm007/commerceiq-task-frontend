<template>
  <div class="form-style">
    <!--Form to submit the message, 
    trigger the "onSubmit" function when form is submitted  -->
    <form @submit="onSubmit">
      <div class="input-group">
        <textarea
          type="text"
          class="form-control"
          rows="2"
          cols="20"
          v-model="message"
          placeholder="Add Message"
        />
        <button class="btn btn-block btn-primary my-btn" type="submit">
          SEND!
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  // Name of the component
  name: "SendMessage",

  // State of this component
  data() {
    return { message: "" };
  },

  // Component methods
  methods: {
    // Method triggered, when the form is submitted. It emits a function to submit a new message
    async onSubmit(e) {
      // Prevent default behaviour to avoid reloading
      e.preventDefault();

      // Checking if the text message is not empty
      if (!this.message || this.message === "") {
        alert("Please add a message!");
        return;
      }

      // Emit it to parent component so the message can be added to the DB
      this.$emit("add-message", this.message);

      // Clear the state
      this.message = "";
    },
  },
};
</script>

<style scoped>
.form-style {
  padding: 0 1.5rem 0 1.7rem;
  background-color: transparent;
  border-top: 1px solid transparent;
  border-bottom-right-radius: 3px;
  border-bottom-left-radius: 3px;
  margin: 2rem;
  margin-left: -1.5rem;
}

.my-btn {
  width: 5rem;
  margin-left: 1rem;
  margin-right: -3.7rem;
}
</style>
