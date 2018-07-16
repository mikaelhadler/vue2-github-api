<template>
  <div class="github-wrapper"
    v-if="user.login">
    <div class="avatar">
      <img
        v-bind:src="user.avatar_url">
    </div>
    <div class="information">
      <div>
        <label for="">{{ user.public_repos }}</label>
        <a :href="user.repos_url">Repositories</a>
      </div>
      <div>
        <label for="">{{ user.followers }}</label>
        <a
          :href="user.following_url">Followers</a>
      </div>
      <div>
        <label for="">{{ user.following }}</label>
        <a
          :href="user.following_url">Following</a>
      </div>
    </div>
    <div>
      <span>Need save this?</span>
      <button>
        click here
      </button>
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
