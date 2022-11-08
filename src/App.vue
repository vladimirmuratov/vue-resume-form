<template>
  <div class="container column">
    <app-menu
        @get-data="getData"
    ></app-menu>

    <app-card
        :title="title"
        :subtitle="subtitle"
        :avatar="avatar"
        :text="text"
    ></app-card>
  </div>

  <app-comments-list></app-comments-list>

</template>

<script>
import AppMenu from "@/components/AppMenu"
import AppCard from "@/components/AppCard"
import AppCommentsList from "@/components/AppCommentsList"

export default {
  data() {
    return {
      title: '',
      subtitle: '',
      avatar: '',
      text: ''
    }
  },
  methods: {
    getData(select, data) {
      switch (select) {
        case 'title':
          this.title = data
          break
        case 'subtitle':
          this.subtitle = data
          break
        case 'avatar':
          this.avatar = data
          break
        case 'text':
          this.text = data
          break
      }
    }
  },
  components: {AppMenu, AppCard, AppCommentsList}
}
</script>

<style scoped>

</style>
