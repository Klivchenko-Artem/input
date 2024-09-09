<template>
  <input type="number" :value="value" @input="updateValue($event.target.value)" />
</template>

<script>
export default {
  props: {
    value: [String, Number]
  },
  methods: {
    updateValue(newValue) {
      this.$emit('input', newValue);
    }
  }
};
</script>