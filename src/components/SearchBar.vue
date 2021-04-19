<template>
  <div><input v-model="message" /></div>
</template>

<script>
import _ from "lodash";

export default {
  name: "SearchBar",
  data() {
    return {
      message: "",
    };
  },
  methods: {},
  watch: {
    message: _.debounce(function () {
      this.$emit("termChange", this.message);
    }, 800),
  },
};
</script>

<style scoped>
input {
  width: 75%;
}

div {
  text-align: center;
  margin: 20px;
}
</style>