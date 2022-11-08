<template>
  <form class="card card-w30" @submit.prevent="submitHandler">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="select">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" minlength="3" v-model.trim="data"></textarea>
    </div>

    <button class="btn primary" :disabled="data.length < 3">Добавить</button>
  </form>
</template>

<script>
export default {
  emits: ['get-data'],
  data() {
    return {
      select: 'title',
      data: ''
    }
  },
  methods: {
    submitHandler() {
      this.$emit('get-data', this.select, this.data)
      this.data = ''
      this.select = 'title'
    }
  }
}
</script>

<style scoped>

</style>
