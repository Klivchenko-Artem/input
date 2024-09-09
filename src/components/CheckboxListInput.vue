<template>
  <div>
    <label v-for="option in options" :key="option">
      <input
        type="checkbox"
        :value="option"
        :checked="value.includes(option)"
        @change="updateValue(option, $event.target.checked)"
      />
      {{ option }}
    </label>
  </div>
</template>

<script>
export default {
  props: {
    value: Array,
    options: Array
  },
  methods: {
    updateValue(option, isChecked) {
      const newValue = isChecked
        ? [...this.value, option]
        : this.value.filter(item => item !== option);
      this.$emit('input', newValue);
    }
  }
};
</script>