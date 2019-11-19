<template>
  <select v-model="localState">
    <option v-for="(state, abbreviation) in states" :value="abbreviation" v-html="state" :key="state"></option>
  </select>
</template>
<script type="text/babel">
export default {
  props: {
    value: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      states: {
        NY: "New York",
        WI: "Wisconsin"
        // + rest of the states
      }
    };
  },
  computed: {
    localState: {
      get() {
        return this.value;
      },
      set(localState) {
        this.$emit("input", localState);
      }
    }
  }
};
</script>