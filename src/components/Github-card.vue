<template>
  <div class="github"
    v-if="user.login">
    <div class="github-avatar">
      <img 
        v-bind:src="user.avatar_url">
    </div>
    <div class="github-information">
      <span>
        {{ user.public_repos }}
        <label>Stars</label>
      </span>
      <span>
        {{ user.followers }}
        <label>Repositories</label>
      </span>
    </div>
  </div>
</template>
<script>
export default {
  name: "GithubCard",
  props: ["user"]
};
</script>
<style scoped>
.github {
  width: 50%;
  margin: 0 auto;
  text-align: center;
  padding: 20px;
}
.github-avatar img {
  max-width: 200px;
}
.github-information {
  display: flex;
  flex-direction: column;
  padding: 2px;
}
.github-information label {
  margin: 0px 1px;
}
</style>
