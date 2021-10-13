<template>
  <div class="paint-volume-form">
    <div class="title mb-4">Рассчитайте объем краски</div>
    <form class="form" @submit.prevent>
      <TextField
        v-model="a"
        type="number"
        placeholder="Заполните поле"
      ></TextField>
      <TextField
        v-model="b"
        type="number"
        placeholder="Заполните поле"
      ></TextField>
      <TextField
        v-model="c"
        type="number"
        placeholder="Заполните поле"
      ></TextField>
      <div class="flex between w-full">
        <div class="calculate" @click="calc">Рассчитать</div>
        <div>{{ res }}</div>
      </div>
    </form>
  </div>
</template>

<script>
import TextField from '../ui/TextField.vue'
export default {
  components: { TextField },
  data: () => ({
    a: '',
    b: '',
    c: '',
    res: '',
  }),
  methods: {
    calc() {
      this.res = Number(this.a) + Number(this.b) + Number(this.c)
    },
  },
}
</script>

<style>
.paint-volume-form {
  margin: 16px;
  display: flex;
  flex-flow: column;
  padding: 16px;
  background: #fff;
  box-shadow: 0 10px 30px 0 rgba(161, 174, 198, 0.5);
}
.paint-volume-form .title {
  font-size: 18px;
}
.paint-volume-form .form {
  display: flex;
  flex-flow: column;
  gap: 12px;
  align-items: flex-start;
}
.paint-volume-form .calculate {
  cursor: pointer;
  color: #e61c36;
  text-decoration: none;
  border-bottom: 2px solid #e61c36;
  padding-bottom: 4px;
  font-weight: 500;
}
@media (max-width: 475px) {
  .paint-volume-form {
    margin: 16px 0 0;
  }
}
</style>
