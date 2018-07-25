<template>
  <div class="error">
    <span>
      {{ errorUpper }}
    </span>
  </div>
</template>
<script>
export default {
  props: ["error"],
  name: "Error",
  computed: {
    errorUpper: function () {
      return this.error.toUpperCase();
    }
  }
};
</script>
<style scoped>
.error span {
  font-weight: 600;
}
</style>

