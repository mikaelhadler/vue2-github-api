<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <GithubSearch
      @searchUser="searchUser"/>
    <GithubCard
      :user="user"/>
    <Error
      :errorList="handlers"
    />
  </div>
</template>

<script>
import axios from "axios";
import GithubSearch from "./Github-search.vue";
import GithubCard from "./Github-card.vue";
import Error from "./Error.vue";

export default {
  name: "Github",
  data() {
    return {
      user: {},
      handlers: [],
      title: "Welcome to github playground api :)"
    };
  },
  methods: {
    searchUser: async function(search) {
      if (search) {
        this.cleanErrorMessages();
        try {
          let res = await axios.get("https://api.github.com/users/" + search);
          this.user = res.data;
        } catch (err) {
          this.user = {};
          this.handlers.push("User not found");
        }
      }
    },
    cleanErrorMessages: function() {
      this.handlers = [];
    }
  },
  components: {
    GithubSearch,
    GithubCard,
    Error
  }
};
</script>
<style scoped>
input.search {
  border-radius: 3px;
}
</style>
