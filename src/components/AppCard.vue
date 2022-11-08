<template>
  <div class="card card-w70">
    <h1 v-if="title">{{ title }}</h1>
    <div class="avatar" v-if="avatar">
      <img :src="avatar">
    </div>
    <h2 v-if="subtitle">{{ subtitle }}</h2>
    <h2 v-if="text">Опыт работы</h2>
    <p v-if="text">{{ text }}</p>
    <h3 v-else-if="!title && !subtitle && !avatar && !text">Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    subtitle: String,
    avatar: String,
    text: String
  }
}
</script>

<style scoped>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
