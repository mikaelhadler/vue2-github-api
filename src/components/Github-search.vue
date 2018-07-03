<template>
  <div class="github-search">
    <input type="text" class="search" placeholder="Your github username"
      v-model="search">
    <button
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
