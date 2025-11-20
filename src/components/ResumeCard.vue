<template>
  <div class="card card-w70">
    <template v-if="resumeBlocks.length">
      <component
        v-for="block in resumeBlocks"
        :key="block.id"
        :is="'resume-' + block.type"
        v-bind="{value: block.value}"
      ></component>
    </template>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import ResumeTitle from '../parts/ResumeTitle.vue'
import ResumeAvatar from '../parts/ResumeAvatar.vue'
import ResumeSubtitle from '../parts/ResumeSubtitle.vue'
import ResumeText from '../parts/ResumeText.vue'
import axios from 'axios'

export default {
  data () {
    return {
      resumeBlocks: []
    }
  },
  mounted () {
    this.loadResume()
  },
  methods: {
    async loadResume () {
      const { data } = await axios.get('https://vue-resume-40fdf-default-rtdb.firebaseio.com/resume.json')
      this.resumeBlocks = Object.keys(data).map((key) => {
        return {
          id: key,
          ...data[key]
        }
      })
    }
  },
  components: {
    ResumeTitle,
    ResumeAvatar,
    ResumeSubtitle,
    ResumeText
  }
}
</script>
