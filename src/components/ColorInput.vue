<template>
  <input type="color" :value="value" @input="updateValue($event.target.value)" />
</template>

<script>
export default {
  props: {
    value: String
  },
  methods: {
    updateValue(newValue) {
      this.$emit('input', newValue);
    }
  }
};
</script>