<template>
  <div class="paint-page">
    <div class="container">
      <div class="title pb-4">{{ paintData.title }}</div>
      <div class="bread flex">
        <NuxtLink to="/">Каталог</NuxtLink>
        <span class="pl-4 pr-4">></span>
        <span>{{ paintData.title }}</span>
      </div>

      <div class="paint-page--columns">
        <div class="left">
          <ImageList :images="mapImgs"></ImageList>
          <div class="paint-stats">
            <div class="title">Характеристики</div>
            <div class="flex col">
              <div class="paint-stats--item">
                ⭐️ Бренд: <span>·········</span> {{ paintData.stats.brand }}
              </div>
              <div class="paint-stats--item">
                ⭐️ Тип: <span>·············</span> {{ paintData.stats.type }}
              </div>
              <div class="paint-stats--item">
                ⭐️ Цвет: <span>···········</span> {{ paintData.stats.color }}
              </div>
            </div>
          </div>
        </div>
        <div class="right">
          <div class="long-title mb-4">
            {{ paintData.longTitle }}
          </div>
          <div class="brand-info">
            <span class="flex-1">Бренд: {{ paintData.brandName }}</span>
            <div class="paint--stock">
              <div v-if="paintData.inStock" class="in-stock">✅ В наличии</div>
              <div v-else class="not-in-stock">❌ Кончилась</div>
            </div>
          </div>

          <PaintTabs :paintData="paintData"></PaintTabs>
          <CalculateVolumeForm></CalculateVolumeForm>
        </div>
      </div>

      <div class="paint-page--columns">
        <div class="flex extra-info-left">
          <img class="flex pr-4" :src="paintData.extraInfo1.img" alt="img" />
          <div class="flex col center">
            <div class="pb-4 font-semi">{{ paintData.extraInfo1.title }}</div>
            <div class="font-secondary">{{ paintData.extraInfo1.descr }}</div>
          </div>
        </div>
        <div class="flex extra-info-right">
          <img class="flex pr-4" :src="paintData.extraInfo2.img" alt="img" />
          <div class="flex col center">
            <div class="pb-4 font-semi">{{ paintData.extraInfo2.title }}</div>
            <div class="font-secondary">{{ paintData.extraInfo2.descr }}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="more-products">
      <div class="container more-products--title">С этим товаром еще покупают</div>
      <ImageSlider>
        <PaintCard
          v-for="(paint, id) in [...paintsList, ...paintsList]"
          :key="id"
          :data="paint"
        ></PaintCard>
      </ImageSlider>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import ImageList from '@/components/ui/ImageList.vue'
import ImageSlider from '@/components/ui/ImageSlider.vue'
import PaintTabs from '@/components/PaintPage/PaintTabs.vue'
import CalculateVolumeForm from '@/components/PaintPage/CalculateVolumeForm.vue'
import PaintCard from '@/components/PaintCard.vue'

export default {
  components: {
    ImageList,
    PaintTabs,
    CalculateVolumeForm,
    ImageSlider,
    PaintCard,
  },
  data: () => ({
    paintData: {},
  }),
  fetch() {
    this.paintData = this.$store.getters['paints/getById'](
      Number(this.$route.params.id)
    )
  },
  computed: {
    ...mapGetters({
      getById: 'paints/getById',
    }),
    mapImgs() {
      return [this.paintData.image, ...this.paintData.images.map((v) => v.src)]
    },
    ...mapGetters({
      paintsList: 'paints/list',
    }),
  },
}
</script>

<style scoped>
.paint-page {
  display: flex;
  flex-flow: column;
  padding: 24px;
}
.paint-page .title {
  font-size: 28px;
  font-weight: 500;
}
.paint-page .bread {
  font-size: 12px;
  margin-bottom: 24px;
}
.paint-page .bread a {
  color: #62aad9;
}

.paint-page--columns {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
  margin-bottom: 40px;
  gap: 40px;
}

.paint-stats {
  margin-top: 20px;
}
.paint-stats .title {
  font-size: 20px;
  margin-bottom: 14px;
}
.paint-stats--item {
  color: #212121;
}
.paint-stats--item span {
  color: #0e8bcd;
  font-size: 18px;
  padding: 0 6px;
}

.long-title {
  font-size: 20px;
}

.brand-info {
  display: flex;
}

.paint--stock {
  display: flex;
  margin-left: 16px;
}
.paint--stock .in-stock {
  color: green;
}
.paint--stock .not-in-stock {
  color: red;
}

.extra-info-right {
  margin-left: 16px;
}

.more-products {
  margin-top: 40px;
}
.more-products--title {
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 20px;
}

@media (max-width: 475px) {
  .paint-page--columns {
    flex-flow: column;
    gap: 16px;
    display: flex;
  }
  .paint-page--columns .left {
    align-items: center;
  }
  .brand-info {
    flex-flow: column;
  }
  .paint--stock {
    margin-left: 0;
    margin-top: 16px;
  }
  .extra-info-right {
    margin-left: 0;
  }
  .extra-info-left, .extra-info-right {
    flex-flow: column;
  }
  .extra-info-left img, .extra-info-right img {
    margin-bottom: 10px;
  }
}
</style>
