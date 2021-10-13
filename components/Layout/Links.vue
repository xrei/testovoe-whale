<template>
  <div class="app-links flex">
    <a v-for="l in links" :key="l.id" :href="'#' + l.name" class="app-link">
      {{ l.name }}
    </a>
  </div>
</template>

<script>
export default {
  data: () => ({
    links: [
      { id: 0, name: 'Проекты' },
      { id: 1, name: 'Новости' },
      { id: 2, name: 'Деятельность' },
      { id: 3, name: 'Где купить' },
      { id: 4, name: 'Контакты' },
      { id: 5, name: 'О компании' },
    ],
  }),
}
</script>

<style scoped>
.app-link {
  color: inherit;
  padding-bottom: 4px;
  border-bottom: 2px solid #1096de;
  margin-right: 14px;
  text-decoration: none;
}
@media (max-width: 475px) {
  .app-link {
    margin-right: 0;
    margin-bottom: 16px;
  }
}
.app-link:last-child {
  margin: 0;
}
</style>
