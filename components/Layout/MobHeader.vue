<template>
  <div class="flex p-4 between mobile-header">
    <div class="flex flex-1 pr-4">
      <img class="flex" src="/logo.png" alt="logo" />
    </div>

    <div class="flex items-center">
      <BurgerButton @click="open = !open"></BurgerButton>
    </div>
    <NavigationDrawer v-model="open" @close="close">
      <div slot="header">
        <img class="flex" src="/logo.png" alt="logo" />
      </div>

      <div class="drawer-container">
        <div class="pb-4" @click.stop="close">
          <CatalogBtn ></CatalogBtn>
        </div>
        <Links class="col flex-1"></Links>

        <div class="mob-mail pb-4">
          <span>Пишите сюда - </span>
          <a href="#">mail@palitranpk.ru</a>
        </div>
        <div class="flex between">
          <div class="flex col">
            <span class="header-phone font-semi">+7 (812) 603-45-00</span>
            <div class="flex header-icons">
              <img class="flex" src="/tg.svg" alt="" />
              <img class="flex" src="/wap.svg" alt="" />
              <img class="flex" src="/viber.svg" alt="" />
            </div>
          </div>

          <div class="flex col contact-phone">
            <span class="font-semi">8 (800) 500-39-57</span>
            <a href="#" class="font-semi">Заказать звонок</a>
          </div>
        </div>
      </div>
    </NavigationDrawer>
  </div>
</template>

<script>
import CatalogBtn from './CatalogBtn.vue'
import Links from './Links.vue'
import NavigationDrawer from '@/components/ui/NavigationDrawer'
import BurgerButton from '@/components/ui/BurgerButton'

export default {
  components: { NavigationDrawer, BurgerButton, Links, CatalogBtn },
  data: () => ({
    open: false,
  }),
  methods: {
    close() {
      this.open = false
    }
  }
}
</script>

<style>
.mobile-header {
  background: #ddd;
}
.drawer-container {
  display: flex;
  flex-flow: column;
  flex: 1;
}
.drawer-container .app-links {
  font-weight: 500;
}
.drawer-container .app-link:hover {

  color: #0088cc;
}
.drawer-container .catalog-button button {
  color: #000;
}

.drawer-container .header-phone {
  color: #000;
  padding-bottom: 4px;
}
.drawer-container .header-icons > img {
  width: 24px;
  height: 24px;
  padding-right: 4px;
}
.drawer-container .contact-phone {
  color: #000;
  justify-content: space-between;
}
.drawer-container .contact-phone a {
  color: #00aa85;
}
.mob-mail span {
  color: #0088cc;
  font-weight: bold;
}
.mob-mail a {
  color: #00aa85;
}
</style>
