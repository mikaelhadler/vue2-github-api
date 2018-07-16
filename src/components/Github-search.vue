<template>
  <div class="github-search">
    <input type="text" class="input" placeholder="Your github username"
      @keyup.enter="$emit('searchUser', search)"
      v-model="search">
    <button class="action"
      @click="$emit('searchUser', search)">
      Send
    </button>
  </div>
</template>
<script>
export default {
  name: "GithubSearch",
  data() {
    return {
      search: ""
    };
  }
};
</script>
