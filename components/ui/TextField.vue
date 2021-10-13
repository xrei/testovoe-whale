<template>
  <div class="text-field">
    <input :value="value" :type="type" v-bind="$attrs"  @input="onInput">
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: [String, Number],
      default: ''
    },
    type: {
      type: String,
      default: 'text'
    }
  },
  methods: {
    onInput(e) {
      this.$emit('input', e.target.value)
    }
  }
}
</script>

<style>
.text-field {
  width: 100%;
  border: 1px solid #C9C9C9;
  color: #000;
  height: 40px;
  display: flex;
}
.text-field input {
  border: 0;
  background: none;
  color: inherit;
  width: 100%;
  height: 100%;
  padding: 8px 14px;
}
</style>