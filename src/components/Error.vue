<template>
  <div>
    <span
      v-for="(error, index) in errorList"
      :key="index">
      {{ error }}
    </span>
  </div>
</template>
<script>
export default {
  props: ["errorList"],
  name: "Error"
};
</script>
