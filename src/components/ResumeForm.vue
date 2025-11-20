<template>
  <form class="card card-w30" @submit.prevent="submitHandler">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" v-model="value" rows="3"></textarea>
    </div>

    <button class="btn primary" type="submit" :disabled="!isValid">Добавить</button>
  </form>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      type: 'title',
      value: ''
    }
  },
  computed: {
    isValid () {
      return this.value.length > 3
    }
  },
  methods: {
    async submitHandler () {
      await axios.post(
        'https://vue-resume-40fdf-default-rtdb.firebaseio.com/resume.json',
        {
          type: this.type,
          value: this.value
        }
      )
      this.value = ''
      this.type = 'title'

      this.$emit('getResume')
    }
  }
}
</script>
