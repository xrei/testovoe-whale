<template>
  <NuxtLink to="/" class="flex overflow-hidden pr-6" v-on="$listeners">
    <div class="catalog-button">
      <button>
        Каталог
      </button>
    </div>
  </NuxtLink>
</template>

<script>
export default {}
</script>

<style>
.catalog-button {
  width: 200px;
  height: 46px;
  margin: 0 0 0 -20px;
  transform: skew(-15deg);
  border: 2px solid #0088cc;
  overflow: hidden;
  position: relative;
}
.catalog-button button {
  cursor: pointer;
  position: absolute;
  transform: skew(15deg);
  left: 18px;
  width: 95%;
  color: #fff;
  background: transparent;
  height: 100%;
  border: 0;
  border-left: 2px solid #0088cc;
  font-weight: 500;
  padding: 0;
}
.catalog-button button a {
  text-decoration: none;
  z-index: 1;
}
.catalog-button button:hover {
  background: #0088cc;
  color: #fff;
}
</style>
