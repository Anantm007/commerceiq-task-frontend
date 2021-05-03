<template>
  <button class="btn btn-dark" @click="$emit('toggle-show-chat')">
    CLICK TO OPEN/CLOSE CHAT!
  </button>
</template>
<script>
export default {
  name: "ShowChat",
};
</script>

<style scoped>
button {
  margin: 6rem auto 0 2rem;
  width: 20rem;
}
</style>
