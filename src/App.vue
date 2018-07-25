<template>
  <div id="app">
    <div class="container">
      <h1>{{ title }}</h1>
      <UserNameSearch
        @searchUser="searchUser"/>
      <Loading v-if="isLoading"/>
      <UserCard
        :user="user"/>
      <h3 v-if="error">{{ error }}</h3>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import UserNameSearch from './components/UserNameSearch';
import UserCard from './components/UserCard';
import Loading from './components/Loading';

export default {
  name: 'Github',
  components: {
    UserNameSearch,
    UserCard,
    Loading,
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
    searchUser(search) {
      this.cleanErrorMessages();
      this.isLoading = true;
      axios
        .get(`https://api.github.com/users/${search}`)
        .then( res => {
          this.user = res.data;
          this.isLoading = false;
        }).catch((e) => {
          this.user = {};
          this.error = e.message;
          this.isLoading = false;
        });
    },

    cleanErrorMessages() {
      this.error = '';
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
