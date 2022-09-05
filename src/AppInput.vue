<template>
  <div class="form-control" :class="{'error': error}">
    <label :for="id">{{ label }}</label>
    <input
      :value="modelValue"
      type="text"
      :id="id"
      :placeholder="placeholder"
      @input="change"
    />
    <small v-if="error">{{ error }}</small>
  </div>
</template>

<script>
export default {
  props: {
    modelValue: String,
    error: String,
    placeholder: String,
    label: String
  },
  emits: ['update:modelValue'],
  data () {
    return {
      id: Math.random()
    }
  },
  methods: {
    change (event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>
