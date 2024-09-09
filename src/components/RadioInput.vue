<template>
  <div>
    <label v-for="option in options" :key="option">
      <input type="radio" :value="option" v-model="modelValue" />
      {{ option }}
    </label>
  </div>
</template>

<script>
export default {
  props: {
    value: String,
    options: Array
  },
  computed: {
    modelValue: {
      get() {
        return this.value;
      },
      set(value) {
        this.$emit('input', value);
      }
    }
  }
};
</script>