<template>
  <div class="container column">
    <resume-form @getResume="getResume"></resume-form>
    <resume-card ref="resumeCard"></resume-card>
  </div>
  <div class="container">
    <resume-comments></resume-comments>
    <app-loader></app-loader>
  </div>
</template>

<script>
import AppLoader from './components/AppLoader.vue'
import ResumeComments from './components/ResumeComments.vue'
import ResumeForm from './components/ResumeForm.vue'
import ResumeCard from './components/ResumeCard.vue'

export default {
  methods: {
    getResume () {
      this.$refs.resumeCard.loadResume()
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
