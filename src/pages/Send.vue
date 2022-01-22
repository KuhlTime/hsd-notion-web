<template>
  <div class="hello">
    <h1>HSD-Community</h1>
    Du hast dich erfolgreich eingeschrieben. Wir bearbeiten nun deine Anfrage.
    <br />
    <h1>🥳 💪</h1>
  </div>
</template>

<script>
import confetti from "canvas-confetti";

export default {
  name: "Home",
  mounted() {
    confetti({
      particleCount: 100,
      spread: 70,
      origin: { y: 0.6 },
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
