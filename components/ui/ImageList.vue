<template>
  <div class="images-list">
    <div class="main-img">
      <img class="flex" :src="renderActive" alt="">
    </div>

    <div class="images-slider">
      <img v-for="(img, id) in images" :key="id" class="flex" :src="img" alt="" @click="setActive(img)" >
    </div>
  </div>
</template>

<script>
export default {
  props: {
    images: {
      type: Array,
      default: () => [],
      required: true,
    }
  },
  data: () => ({
    activeImg: ''
  }),
  computed: {
    renderActive() {
      return this.activeImg || this.images[0]
    }
  },
  methods: {
    setActive(img) {
      this.activeImg = img
    }
  }
}
</script>

<style>
.images-list {
  display: flex;
  flex-flow: column;
}
.main-img {
  display: flex;
  justify-content: center;
}
.main-img img {
  max-width: 100%;
  max-height: 300px;
}

.images-slider {
  display: flex;
  gap: 16px;
  white-space: nowrap;
  flex-wrap: nowrap;
  overflow: hidden;
  overflow-x: scroll;
}
.images-slider img {
  display: flex;
  max-width: 140px;
}
.images-slider img:hover {
  border: 1px solid grey;
}

@media (max-width: 475px) {
  .images-list {
    max-width: 100%;
  }
}
</style>