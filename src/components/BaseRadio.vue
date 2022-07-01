<template>
  <input
    type="radio"
    :checked="modelValue === value"
    :value="value"
    @change="$emit('update:modelValue', value)"
    v-bind="$attrs"
  />
  <label v-if="label">{{ label }}</label>
</template>

<script>
export default {
  name: 'BaseRadio',
  props: {
    label: {
      type: String,
      default: ''
    },
    modelValue: {
      type: Boolean,
      default: false
    },
    value: {
      type: [String, Number],
      required: true
    }
  }
}
</script>
