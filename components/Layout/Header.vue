<template>
  <div class="app-header">
    <div class="overlay-bar"></div>
    <div class="container app-header--content">
      <div class="flex between pb-4">
        <div class="header-logo">
          <img class="flex" src="/logo.png" alt="logo" />
        </div>
        <div class="flex items-center header-email pr-6">
          <span class="at-icon">@</span>
          <a href="#">mail@palitranpk.ru</a>
        </div>
        <div class="flex col pr-6">
          <span class="header-phone font-semi">+7 (812) 603-45-00</span>
          <div class="flex header-icons">
            <img class="flex" src="/tg.svg" alt="" />
            <img class="flex" src="/wap.svg" alt="" />
            <img class="flex" src="/viber.svg" alt="" />
          </div>
        </div>
        <div class="flex items-center phone-call pr-6">
          <img class="flex" src="/call.svg" alt="" />
          <div class="flex col">
            <span class="phone-call--title font-semi">8 (800) 500-39-57</span>
            <span class="phone-call--sub">Звонок по рф бесплатный</span>
          </div>
        </div>
        <div class="flex items-center order-call">
          <a href="#" class="font-semi">Заказать звонок</a>
        </div>
      </div>
      <div class="flex between">
        <CatalogBtn></CatalogBtn>
        <Links class="items-center pr-4"></Links>
        <div class="overflow-hidden">
          <div class="search-button">
            <button>Подобрать</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Links from './Links.vue'
import CatalogBtn from './CatalogBtn.vue'

export default {
  components: { Links,CatalogBtn}
}
</script>

<style>
.app-header {
  min-height: 280px;
  max-height: 280px;
  height: 100%;
  width: 100%;
  background: #363a3f;
  display: flex;
  flex-flow: column;
}
.app-header .overlay-bar {
  width: 100%;
  height: 40px;
  filter: blur(10);
  background: #1f3242;
}
.app-header .app-header--content {
  display: flex;
  flex-flow: column;
  justify-content: space-around;
  padding-top: 30px;
  padding-bottom: 48px;
  flex: 1;
}
.app-header .header-logo {
  padding-right: 24px;
}
.app-header .header-email {
  color: #02a481;
}
.app-header .header-email .at-icon {
  font-size: 24px;
  padding-right: 4px;
}
.app-header .header-phone {
  color: #fff;
  padding-bottom: 4px;
}
.app-header .header-icons > img {
  width: 16px;
  height: 16px;
  padding-right: 4px;
}
.app-header .phone-call img {
  width: 20px;
  height: 20px;
  padding-right: 4px;
}
.app-header .phone-call .phone-call--title {
  color: #fff;
  margin-bottom: 4px;
}
.app-header .phone-call .phone-call--sub {
  color: #00aa85;
}
.app-header .order-call a {
  text-decoration: none;
  color: #fff;
  padding-bottom: 4px;
  border-bottom: 2px solid red;
}

.app-header .app-link {
  color: #fff;
}

.search-button {
  width: 190px;
  height: 46px;
  margin-left: 10px;
  transform: skew(-15deg);
  transform-origin: bottom;
  border: 2px solid #00AA85;
  overflow: hidden;
  position: relative;
}
.search-button button {
  cursor: pointer;
  position: absolute;
  transform: skew(15deg);
  left: -6px;
  width: 101%;
  color: #00AA85;
  font-weight: 500;
  height: 100%;
  border: 0;
  border-right: 2px solid #00AA85;
  background: transparent;
  padding: 0;
}
.search-button button:hover {
  background: #00AA85;
  color: #fff;
}
</style>
