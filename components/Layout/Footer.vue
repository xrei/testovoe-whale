<template>
  <div class="app-footer">
    <div class="container footer-grid">
      <div class="flex col">
        <div class="flex mb-4">
          <img class="flex" src="/logo.png" alt="" style="height: 30px" />
        </div>
        <div class="pb-2">(c) 2015 НПК</div>
        <div>Все права защищены.</div>
      </div>

      <div class="flex col">
        <div class="col-title">Главная</div>
        <a href="#">Проекты</a>
        <a href="#">Новости</a>
        <a href="#">Деятельность</a>
        <a href="#">Контакты</a>
        <a href="#">Купить</a>
      </div>
      <div class="flex col">
        <div class="col-title">Компания</div>
        <a href="#">О компании</a>
        <a href="#">Производство</a>
        <a href="#">Доставка и оплата</a>
        <a href="#">Наши бренды</a>
        <a href="#">Сертификаты</a>
        <a href="#">Вакухи</a>
        <a href="#">Реквизиты</a>
        <a href="#">Отзывы</a>
      </div>
      <div class="flex col">
        <div class="col-title">Каталог</div>
        <a href="#">лорем ипсум</a>
        <a href="#">лорем ипсум</a>
        <a href="#">лорем ипсум</a>
        <a href="#">лорем ипсум</a>
        <a href="#">лорем ипсум</a>
      </div>
      <div class="flex col footer-grid--last">
        <div class="flex mb-4">
          <div class="flex items-center mr-2">📞</div>
          <div class="flex col">
            <span class="font-semi text-white">8 (800) 500-39-57</span>
            <span class="font-xs">Звонок по рф бесплатный</span>
          </div>
        </div>
        <div class="flex mb-4">
          <div class="flex items-center mr-2">✉️</div>
          <div class="flex col">
            <span class="text-white font-semi">+7 (812) 603-45-00</span>
            <div class="flex footer-icons">
              <img class="flex" src="/tg.svg" alt="" />
              <img class="flex" src="/wap.svg" alt="" />
              <img class="flex" src="/viber.svg" alt="" />
            </div>
          </div>
        </div>
        <div class="flex items-center">
          <span class="mr-2">📧</span>
          <a href="#">mail@palitranpk.ru</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.app-footer {
  position: relative;
  background: #00537d;
  padding: 40px 0;
  color: #d7dfe5;
}
.app-footer .col-title {
  color: #fff;
  font-size: 18px;
  font-weight: 500;
  padding-bottom: 10px;
}
.app-footer a {
  color: inherit;
  padding-bottom: 6px;
}
.app-footer a:hover {
  color: #fff;
}
.app-footer a:last-child {
  padding: 0;
}
.footer-icons > img {
  width: 16px;
  height: 16px;
  padding-right: 4px;
}
.footer-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
}

@media (max-width: 475px) {
  .footer-grid {
    gap: 20px;
    grid-template-columns: 1fr 1fr;
    justify-items: center;
  }
  .footer-grid--last {
    grid-column: span 2;
  }
}
</style>
