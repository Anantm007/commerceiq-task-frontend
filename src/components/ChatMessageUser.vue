<template>
  <div class="chat">
    <div class="chat-body">
      <div class="chat-content">
        {{ message.text }} <br /><br />

        {{ new Date(message.timestamp).toLocaleDateString() }}:
        {{
          new Date(message.timestamp).toLocaleTimeString(undefined, {
            timeZone: "Asia/Kolkata",
          })
        }}
        (IST)
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // Name of the component
  name: "ChatMessageAdmin",

  // Props received from the parent
  props: {
    message: Object,
  },
};
</script>

<style scoped>
.chat-body {
  display: block;
  margin: 0 -1rem 0 0;
  overflow: hidden;
}

.chat-body:first-child {
  margin-top: 0;
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
  margin-left: 30px;
}

.chat-left .chat-content {
  float: left;
  margin: 0 0 0.625rem 20px;
  color: #76838f;
  background-color: #dfe9ef;
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
