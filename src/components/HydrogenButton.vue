<template>
  <button @click="clickHandler" :disabled="disabled" :class="classes">
    {{ title }}
    <slot />
  </button>
</template>

<script>
export default {
  name: "HydrogenButton",
  props: {
    title: {
      type: String,
      default: "",
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    flavour: {
      type: String,
      default: "default", // default, primary, secondary
    },
    fullWidth: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    classes() {
      return {
        [this.flavour]: true,
        "full-width": this.fullWidth,
      };
    },
  },
  emits: ["click"],
  methods: {
    clickHandler() {
      this.$emit("click");
    },
  },
};
</script>

<style scoped>
/* GERNERAL */

button {
  /* Position */
  padding: 10px 12px;

  /* Display */
  box-sizing: border-box;

  /* Style */
  border: none;
  border-radius: 4px;

  /* Transition */
  transition: all ease-in-out 120ms;

  /* Interaction */
  cursor: pointer;
  user-select: none;
}

button.full-width {
  /* Display */
  width: 100%;
}

button:disabled {
  /* Style */
  text-decoration: line-through;

  /* Interaction */
  cursor: not-allowed;
}

/* DEFAULT STYLE */

button.default {
  /* Style */
  color: black;
  background-color: transparent;
}

button.default:hover {
  /* Style */
  color: white;
  background-color: black;
}

button.default:disabled {
  /* Style */
  color: rgb(180, 180, 180);
  background-color: transparent;
}

button.default:active:not(:disabled) {
  /* Style */
  background-color: rgb(140, 140, 140);
}

/* PRIMARY STYLE */

button.primary {
  /* Style */
  color: white;
  background-color: black;
}

button.primary:hover {
  /* Style */
  background-color: rgb(80, 80, 80);
}

button.primary:disabled {
  /* Style */
  background-color: rgb(80, 80, 80);
}

button.primary:active:not(:disabled) {
  /* Style */
  background-color: rgb(140, 140, 140);
}

/* SECONDARY STYLE */

button.secondary {
  /* Style */
  color: black;
  background-color: transparent;
  box-shadow: 0 0 0 1px rgb(229, 229, 229);
}

button.secondary:hover {
  /* Style */
  background-color: rgb(229, 229, 229);
  box-shadow: 0 0 0 1px black;
}

button.secondary:disabled {
  /* Style */
  color: rgb(180, 180, 180);
  background-color: transparent;
  box-shadow: 0 0 0 1px rgb(229, 229, 229);
}

button.secondary:active:not(:disabled) {
  /* Style */
  color: white;
  background-color: rgb(140, 140, 140);
}
</style>
