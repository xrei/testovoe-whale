<template>
  <div class="container main-page">
    <div class="paintings-list">
      <PaintCard
        v-for="paint in paintsList"
        :key="paint.id"
        isStatic
        :data="paint"
      ></PaintCard>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import PaintCard from '@/components/PaintCard.vue'

export default {
  components: { PaintCard },
  computed: {
    ...mapGetters({
      paintsList: 'paints/list',
    }),
  },
}
</script>

<style scoped>
.main-page {
  padding: 32px 16px;
}

.paintings-list {
  display: flex;
  gap: 24px;
  flex-wrap: wrap;
}
@media (max-width: 475px) {
  .main-page {
    padding: 16px;
  }
  .paintings-list {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
  }
}
</style>
