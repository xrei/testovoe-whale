<template>
  <div class="paint-tabs">
    <div class="paint-tabs--head">
      <div
        :class="{
          'paint-tabs--head-item': true,
          active: activeTab === 0,
        }"
        @click="setTab(0)"
      >
        Описание
      </div>
      <div
        :class="{
          'paint-tabs--head-item': true,
          active: activeTab === 1,
        }"
        @click="setTab(1)"
      >
        Характеристики
      </div>
      <div
        :class="{
          'paint-tabs--head-item': true,
          active: activeTab === 2,
        }"
        @click="setTab(2)"
      >
        Документы
      </div>
    </div>
    <div v-if="activeTab === 0" class="paint-tabs--content descr">
      {{ paintData.description }}
    </div>
    <div v-if="activeTab === 1" class="paint-tabs--content stats">
      <div class="stats--item">
        Бренд: <span>{{ paintData.stats.brand }}</span>
      </div>
      <div class="stats--item">
        Тип: <span>{{ paintData.stats.type }}</span>
      </div>
      <div class="stats--item">
        Цвет: <span>{{ paintData.stats.color }}</span>
      </div>
    </div>
    <div v-if="activeTab === 2" class="paint-tabs--content">Документов нет</div>
  </div>
</template>

<script>
export default {
  props: {
    paintData: {
      type: Object,
      default: () => ({}),
    },
  },
  data: () => ({
    activeTab: 0,
  }),

  methods: {
    setTab(tab) {
      this.activeTab = tab
    },
  },
}
</script>

<style>
.paint-tabs {
  margin-top: 40px;
  display: flex;
  flex-flow: column;
  background: #fff;
  padding: 16px;
  box-shadow: 0 15px 30px 0 rgba(161, 174, 198, 0.2);
}
.paint-tabs--head {
  display: flex;
  align-items: flex-end;
  margin-bottom: 16px;
}
.paint-tabs--head-item {
  color: #6badda;
  text-decoration: underline;
  text-decoration-style: dotted;
  margin-right: 20px;
  cursor: pointer;
  transition: all 0.2s ease;
}
.paint-tabs--head-item.active,
.paint-tabs--head-item:hover {
  color: #e61c36;
  text-decoration: none;
  border-bottom: 2px solid #e61c36;
  padding-bottom: 4px;
  font-weight: 500;
}
.paint-tabs--content {
  color: #6b6b6b;
}
.paint-tabs--content.stats .stats--item {
  margin-bottom: 16px;
}
.paint-tabs--content.stats .stats--item span {
  color: #000;
}
@media (max-width: 425px) {
  .paint-tabs--head {
    flex-wrap: wrap;
  }
  .paint-tabs--head-item:not(:last-child) {
    margin-bottom: 10px;
  }
}
</style>
