<template>
  <div class="error">
    <span>
      {{ error | upperCase }}
    </span>
  </div>
</template>
<script>
export default {
  props: ["error"],
  name: "Error",
  filters: {
    upperCase: function (value) {
      return value.toUpperCase();
    }
  }
};
</script>
<style scoped>
.error span {
  font-weight: 600;
}
</style>

