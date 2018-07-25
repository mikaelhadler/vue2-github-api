<template>
  <div id="app">
    <div class="container">
      <h1>{{ title }}</h1>
      <github-search
        @searchUser="searchUser"/>
      <github-card
        :user="user"/>
        <h3 v-if="error">{{ error }}</h3>
        <loading v-if="isLoading"></loading>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import githubSearch from './components/githubSearch';
import githubCard from './components/githubCard';
import loading from './components/loading';

export default {
  name: 'Github',
  components: {
    githubSearch,
    githubCard,
    loading,
  },

  data() {
    return {
      user: {},
      error: '',
      title: 'Welcome to github playground api :)',
      isLoading: false,
    };
  },

  methods: {
    async searchUser(search) {
      this.cleanErrorMessages();
      this.isLoading = true;

      try {
        const { data } = await axios.get(`https://api.github.com/users/${search}`);

        this.user = data;
        this.isLoading = false;

        return true;
      } catch (e) {
        this.user = {};
        this.error = e.message;
        this.isLoading = false;

        return false;
      }
    },

    cleanErrorMessages() {
      this.error = '';
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input.search {
  border-radius: 3px;
}
</style>


<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
