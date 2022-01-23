<template>
  <div id="spinner"></div>
</template>

<script>
export default {
  name: "HydrogenSpinner",
};
</script>

<style scoped>
#spinner {
  /* Display */
  display: inline-block;
  width: 20px;
  height: 20px;

  /* Style */
  border: 4px solid rgb(229, 229, 229);
  border-right: 4px solid black;
  border-radius: 50%;

  /* Animation */
  animation: spinner 1s linear infinite;
}

@keyframes spinner {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>
