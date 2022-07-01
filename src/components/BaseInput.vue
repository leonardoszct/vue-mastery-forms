<template>
  <label
    :for="uuid"
    v-if="label"
  >{{ label }}</label>
  <input
    :id="uuid"
    :aria-describedby="errorID"
    :aria-invalid="error ? true : null"
    v-bind="$attrs"
    :placeholder="label"
    class="field"
    :class="{
      hasError: error
    }"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  >
  <p
    :id="errorID"
    aria-live="assertive"
    v-if="error"
    class="errorMessage"
  >
    {{ error }}
  </p>
</template>

<script>
import UniqueID from '../features/UniqueID'

export default {
  name: 'BaseInput',
  props: {
    label: {
      type: String,
      default: ''
    },
    modelValue: {
      type: [String, Number],
      default: ''
    },
    error: {
      type: String,
      default: ''
    }
  },
  setup () {
    const uuid = UniqueID().getID()
    return {
      uuid
    }
  },
  computed: {
    errorID () {
      return this.error ? `${this.uuid}-error` : null
    }
  }
}
</script>
