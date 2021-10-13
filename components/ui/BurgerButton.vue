<template>
  <div
    class="burger-button"
    :class="{ active }"
    v-bind="$attrs"
    v-on="$listeners"
  >
    <div class="burger-button__icon" :style="{ width: size + 'px' }">
      <svg viewBox="0 0 20 9">
        <path
          fill-rule="evenodd"
          clip-rule="evenodd"
          d="M0.769531 1.3076C0.769531 0.797797 1.18281 0.384521 1.69261 0.384521H18.308C18.8178 0.384521 19.2311 0.797797 19.2311 1.3076C19.2311 1.8174 18.8178 2.23068 18.308 2.23068H1.69261C1.18281 2.23068 0.769531 1.8174 0.769531 1.3076ZM0.769531 7.76914C0.769531 7.25934 1.18281 6.84606 1.69261 6.84606H12.7695C13.2793 6.84606 13.6926 7.25934 13.6926 7.76914C13.6926 8.27894 13.2793 8.69221 12.7695 8.69221H1.69261C1.18281 8.69221 0.769531 8.27894 0.769531 7.76914Z"
        />
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  inheritAttrs: false,
  props: {
    active: {
      type: Boolean,
      default: false,
    },
    size: {
      type: [String, Number],
      default: 24,
    },
  },
}
</script>

<style scoped>
.burger-button {
  cursor: pointer;
  position: relative;
  display: block;
  pointer-events: all;
  color: #fff;
}
.burger-button svg path {
  transition: 0.2s cubic-bezier(0.39, 0.575, 0.565, 1);
}
.burger-button:hover svg path,
.burger-button.active svg path {
  d: path(
    'M0.961914 1.11522C0.961914 0.605414 1.37519 0.192139 1.88499 0.192139H18.5004C19.0102 0.192139 19.4235 0.605414 19.4235 1.11522C19.4235 1.62502 19.0102 2.03829 18.5004 2.03829H1.88499C1.37519 2.03829 0.961914 1.62502 0.961914 1.11522ZM0.961914 7.57675C0.961914 7.06695 1.37519 6.65368 1.88499 6.65368H18.5004C18.5004 6.65368 19.4235 6.65368 19.4235 7.5C19.4235 8.49983 18.5004 8.49983 18.5004 8.49983H1.88499C1.37519 8.49983 0.961914 8.08656 0.961914 7.57675Z'
  );
}
</style>
