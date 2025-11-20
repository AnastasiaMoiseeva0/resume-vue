<template>
  <div class="card card-w70">
    <resume-title></resume-title>
    <resume-avatar></resume-avatar>
    <resume-subtitle></resume-subtitle>
    <resume-text></resume-text>
    <h3>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import ResumeTitle from '../parts/ResumeTitle.vue'
import ResumeAvatar from '../parts/ResumeAvatar.vue'
import ResumeSubtitle from '../parts/ResumeSubtitle.vue'
import ResumeText from '../parts/ResumeText.vue'

export default {
  components: {
    ResumeTitle,
    ResumeAvatar,
    ResumeSubtitle,
    ResumeText
  }
}
</script>
