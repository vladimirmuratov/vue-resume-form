<template>
  <div class="container">
    <p>
      <button class="btn primary" @click="getComments">Загрузить комментарии</button>
    </p>

    <app-loader v-if="isLoading"></app-loader>

    <app-comment v-else :key="comment.id" v-for="comment in comments" :comment="comment"></app-comment>
  </div>
</template>

<script>
import AppLoader from './AppLoader'
import AppComment from "@/components/AppComment"

export default {
  data() {
    return {
      comments: [],
      isLoading: false
    }
  },
  methods: {
    async getComments() {
      try {
        this.isLoading = true
        const response = (await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42', {
          method: 'GET',
          headers: {
            'Content-Type': 'application/json'
          }
        }))

        if (response.status === 200) {
          this.comments = await response.json()
          this.isLoading = false
        } else {
          throw new Error('Ошибка сервера!')
        }

      } catch (e) {
        this.isLoading = false
        console.log(e.message)
      }
    }
  },
  components: {AppLoader, AppComment}
}
</script>

<style scoped>

</style>
