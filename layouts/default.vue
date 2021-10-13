<template>
  <div>
    <div class="main-layout">
      <Header class="hidden-mobile"></Header>
      <MobHeader class="hidden-desktop"></MobHeader>
      <Nuxt></Nuxt>
      <Footer></Footer>
    </div>
  </div>
</template>

<script>
import Header from '@/components/Layout/Header.vue'
import Footer from '@/components/Layout/Footer.vue'
import MobHeader from '@/components/Layout/MobHeader.vue'

export default {
  components: { Header, MobHeader, Footer },
}
</script>

<style>
.main-layout {
  display: flex;
  flex-flow: column;
  width: 100%;
  min-height: 100vh;
}

@media (max-width: 475px) {
  .hidden-mobile {
    display: none;
  }

  .hidden-desktop {
    display: flex;
  }
}
@media (min-width: 476px) {
  .hidden-desktop {
    display: none;
  }
  .hidden-mobile {
    display: flex;
  }
}
</style>
