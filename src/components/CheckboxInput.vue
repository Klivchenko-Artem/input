<template>
  <input type="checkbox" :checked="value" @change="updateValue($event.target.checked)" />
</template>

<script>
export default {
  props: {
    value: Boolean
  },
  methods: {
    updateValue(newValue) {
      this.$emit('input', newValue);
    }
  }
};
</script>