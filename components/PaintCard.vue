<template>
  <NuxtLink
    :to="{ name: 'paint-id', params: { id: data.id } }"
    :class="['paint-card', isStatic]"
  >
    <div class="paint-card--img">
      <img class="flex" :src="data.image" alt="" />
    </div>
    <div class="paint-card--title pb-4 flex flex-1 center">
      {{ data.title }}
    </div>
    <div class="paint-card--brand">
      {{ data.brandName }}
    </div>
    <div class="paint-card--stock">
      <div v-if="data.inStock" class="in-stock">
        ✅ В наличии
      </div>
      <div v-else class="not-in-stock">
        ❌ Кончилась
      </div>
    </div>
  </NuxtLink>
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
      default: () => ({}),
    },
    isStatic: Boolean,
  },
}
</script>

<style scoped>
.paint-card {
  display: flex;
  flex-flow: column;
  padding: 16px;
  max-width: 280px;
  width: 100%;
  color: #000;
  text-decoration: none;
  text-align: center;
}
.paint-card.static, .paint-card:hover {
  transition: all .2s ease;
  background: #fff;
  box-shadow: 0px 6px 12px rgba(150, 162, 180, 0.36);
}
.paint-card--title {
  white-space: normal;
}

.paint-card--img {
  display: flex;
  justify-content: center;
}
.paint-card--img img {
  max-width: 200px;
}

.paint-card--brand {
  color: #C9C9C9;
}

.paint-card--stock {
  margin-top: 16px;
  display: flex;
  justify-content: center;
}
.paint-card--stock .in-stock {
  color: green;
}
.paint-card--stock .not-in-stock {
  color: red;
}

@media (max-width: 475px) {
  .paint-card {
    padding: 8px;
  }
}
@media (max-width: 375px) {
  .paint-card--img img {
  max-width: 160px;
}
}
</style>
