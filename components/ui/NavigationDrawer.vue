<template>
  <div class="navigation-drawer">
    <Transition name="fade" mode="out-in">
      <div
        v-show="show"
        class="navigation-drawer__backdrop"
        @click="$emit('close')"
      ></div>
    </Transition>

    <div
      class="navigation-drawer__panel"
      :class="{ visible: show }"
      :style="{ height }"
    >
      <div class="navigation-drawer__header">
        <slot name="header">
          <p>{{ title }}</p>
        </slot>
        <div class="navigation-drawer__closer" @click="$emit('close')">
          <span>X</span>
        </div>
      </div>
      <div class="navigation-drawer__content">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Boolean,
      default: false,
    },
    title: {
      type: String,
      default: 'Палитра',
    },
  },
  data() {
    return {
      show: this.value,
      height: '100vh',
    }
  },
  watch: {
    value(value) {
      this.show = this.value
      document.body.style.overflowY = value ? 'hidden' : ''
    },
  },
  mounted() {
    this.$nextTick(() => {
      this.onResize()

      window.addEventListener('resize', this.onResize)
    })
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.onResize)
    document.body.style.overflowY = ''
  },
  methods: {
    onResize() {
      this.height = window.innerHeight
    },
  },
}
</script>

<style scoped>
.navigation-drawer__panel {
  background-color: #fff;
  position: absolute;
  left: -25em;
  top: 0;
  width: 300px;
  transition: 0.2s;
  visibility: hidden;
  opacity: 0;
  display: flex;
  flex-flow: column;
  pointer-events: none;
}
.navigation-drawer__panel.visible {
  left: 0;
  z-index: 10000;
  opacity: 1;
  visibility: visible;
  pointer-events: all;
  overflow-y: auto;
}
/* .navigation-drawer__header,
.navigation-drawer__content {
  width: 100%;
} */

.navigation-drawer__header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px;
}

.navigation-drawer__title,
.navigation-drawer__closer {
  padding: 28px 30px;
}

.navigation-drawer__title {
  color: #000;
}

.navigation-drawer__closer {
  cursor: pointer;
  text-align: center;
}

.navigation-drawer__content {
  display: flex;
  flex-direction: column;
  flex: 1 1 auto;
  padding: 10px;
}

.navigation-drawer__backdrop {
  position: fixed;
  width: 100vw;
  height: 100vh;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 10000;
}

@media (max-width: 480px) {
  .navigation-drawer__panel {
    width: 75vw;
  }
}
</style>
