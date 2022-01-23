<template>
  <div class="hello">
    <h1>HSD-Community<br />Bachelor EI</h1>
    <p>👩‍🎓 ONLYStudents 👨‍🎓</p>
    Du möchtest gerne bei unserem Notion Workspace mitmachen?
    <br />
    <br />
    Gebe einfach deine Hochschule Addresse ein und wir senden dir eine
    Einladung.
    <br />
    <br />

    <HydrogenInput
      v-model="email"
      @submit="submit()"
      style="max-width: 40%; width: 100%"
      placeholder="vorname.nachname"
    />
    <span style="margin-left: 4px"> @study.hs-duesseldorf.de </span>
    <br />
    <br />
    <HydrogenSpinner v-if="loading"></HydrogenSpinner>
    <HydrogenButton
      v-if="!loading"
      :disabled="!valid"
      @click="submit()"
      flavour="primary"
      title="Einschreiben"
    />

    <br />
    <br />
    <p style="font-size: 12px; color: grey">
      Das senden der Einladung kann einige Tage dauern
    </p>
    <p style="font-size: 12px; color: red" v-if="error !== undefined">
      {{ error }}
    </p>
  </div>
</template>

<script>
import HydrogenInput from "../components/HydrogenInput";
import HydrogenButton from "../components/HydrogenButton";
import HydrogenSpinner from "../components/HydrogenSpinner.vue";

export default {
  name: "Home",
  components: { HydrogenInput, HydrogenButton, HydrogenSpinner },
  data() {
    return {
      email: "",
      error: undefined,
      loading: false,
    };
  },
  methods: {
    registerEmail() {
      this.loading = true;

      fetch("https://hsd-notion-api.herokuapp.com/user", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          email: this.email + "@study.hs-duesseldorf.de",
        }),
      })
        .then((res) => res.text())
        .then((text) => {
          console.log(text);
          this.$emit("submit");
          this.loading = false;
          this.error = undefined;
        })
        .catch((error) => {
          console.error(error);
          this.loading = false;
          this.error = error.message;
        });
    },
    submit() {
      if (this.valid) {
        this.registerEmail(this.email);
      }
    },
  },
  computed: {
    valid() {
      return this.email.split(".").length === 2;
    },
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
