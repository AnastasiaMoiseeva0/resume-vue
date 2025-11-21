<template>
  <div class="container column">
    <resume-form @getResume="getResume"></resume-form>
    <resume-card ref="resumeCard"></resume-card>
  </div>
  <div class="container">
    <app-loader v-if="loading"></app-loader>
    <resume-comments
      :comments="comments"
      @load-comments="getComments"
    ></resume-comments>
  </div>
</template>

<script>
import AppLoader from './components/AppLoader.vue'
import ResumeComments from './components/ResumeComments.vue'
import ResumeForm from './components/ResumeForm.vue'
import ResumeCard from './components/ResumeCard.vue'
import axios from 'axios'

export default {
  data () {
    return {
      comments: [],
      loading: false
    }
  },
  methods: {
    getResume () {
      this.$refs.resumeCard.loadResume()
    },
    async getComments () {
      this.loading = true
      const res = await axios.get('https://jsonplaceholder.typicode.com/comments', {
        params: { _limit: 42 }
      })
      this.comments = res.data
      this.loading = false
    }
  },
  components: {
    AppLoader,
    ResumeComments,
    ResumeForm,
    ResumeCard
  }
}
</script>

<style>
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
