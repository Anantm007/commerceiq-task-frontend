<template>
  <div class="chat-left">
    <div class="chat-body">
      <div class="chat-content">
        <p>
          {{ message.text }} <br /><br />
          {{ new Date(message.timestamp).toLocaleDateString() }}
          <span
            v-if="
              message.text !==
                'WELCOME TO THE CHAT APP, YOU CAN ADD A NEW MESSAGE BY TYPING IN THE BOX BELOW. ALL MESSAGES WILL BE DISPLAYED BELOW!'
            "
          >
            : {{ message.timestamp.toString().substr(11, 8) }} (GMT)
          </span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // Name of the component
  name: "ChatMessageAdmin",

  // Message object recieved from parent
  props: {
    message: Object,
  },
};
</script>

<style scoped>
.chat-body {
  display: block;
  overflow: hidden;
  max-width: 17rem;
}

.chat-content {
  position: relative;
  display: block;
  float: right;
  padding: 8px 15px;
  margin: 0 20px 0.625rem 0;
  clear: both;
  color: #fff;
  background-color: #62a8ea;
  border-radius: 4px;
  -webkit-box-shadow: 0 1px 4px 0 rgba(0, 0, 0, 0.37);
  box-shadow: 0 1px 4px 0 rgba(0, 0, 0, 0.37);
}

.chat-content:before {
  position: absolute;
  top: 0.625rem;
  right: -0.625rem;
  width: 0;
  height: 0;
  content: "";
  border: 5px solid transparent;
  border-left-color: #62a8ea;
}

.chat-content > p:last-child {
  margin-bottom: 0;
}

.chat-left .chat-body {
  margin-right: 0;
  margin-left: 2px;
}

.chat-left .chat-content {
  float: left;
  margin: 0 0 0.625rem -10px;
  color: #76838f;
  background-color: #f4f4f4;
  color: #000;
}

.chat-left .chat-content:before {
  right: auto;
  left: -0.625rem;
  border-right-color: #dfe9ef;
  border-left-color: transparent;
}

.chat-left {
  color: #a3afb7;
}
</style>
