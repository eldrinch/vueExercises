<template>
  <h1>User {{ $route.params.userId }}</h1>
</template>

<script>
export default {
  created() {
    console.log(this.$route);
  },
};
</script>
<style></style>
