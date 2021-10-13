<template>
  <div class="image-slider">
    <div class="overlay overlay-left">
      <div class="prev" @click="prev">&#10094;</div>
    </div>
    <div class="overlay overlay-right">
      <div class="next" @click="next">&#10095;</div>
    </div>
    <div ref="container" class="image-slider--cont">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    prev() {
      const el = this.$refs.container
      el.scrollTo({
        top: 0,
        left: el.scrollLeft -= 100,
        behavior: 'smooth'
      });
    },
    next() {
      const el = this.$refs.container
      el.scrollTo({
        top: 0,
        left: Math.max(el.scrollLeft += 100, el.clientWidth),
        behavior: 'smooth',
      })
    },
  },
}
</script>

<style>
.image-slider {
  width: 100%;
  position: relative;
  overflow: hidden;
}
.image-slider .overlay {
  position: absolute;
  width: 150px;
  height: 100%;
  bottom: 0;
  display: flex;
}
.image-slider .overlay-left {
  align-items: center;
  justify-content: flex-end;
  left: 0;
  background: linear-gradient(
    to right,
    rgba(255, 255, 255, 1) 0%,
    rgba(255, 255, 58, 0) 100%
  );
}
.image-slider .overlay-right {
  align-items: center;
  right: 0;
  background: linear-gradient(
    to left,
    rgba(255, 255, 255, 1) 0%,
    rgba(255, 255, 58, 0) 100%
  );
}

.prev,
.next {
  user-select: none;
  border-radius: 50%;
  padding: 10px 16px;
  cursor: pointer;
  background-color: rgba(0, 0, 0, 0.2);
  font-size: 30px;
}
.prev:hover,
.next:hover {
  color: #fff;
  background-color: rgba(0, 0, 0, 0.5);
}

.image-slider--cont {
  padding: 10px 40px;
  display: flex;
  flex-wrap: nowrap;
  overflow-x: auto;
  gap: 16px;
}

@media (max-width: 475px) {
  .image-slider .overlay {
    width: 40px;
  }

  .prev, .next {
    padding: 6px 10px;
    font-size: 20px;
  }
}
</style>
