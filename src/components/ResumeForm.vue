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
      <small v-if="errors.value">{{ errors.value }}</small>
    </div>

    <button class="btn primary" type="submit">Добавить</button>
  </form>
</template>

<script>
export default {
  data () {
    return {
      type: 'title',
      value: '',
      errors: {
        value: null
      }
    }
  },
  methods: {
    formIsValid () {
      let isValid = true

      if (this.value.length === 0) {
        this.errors.value = 'Введите значение'
        isValid = false
      } else {
        this.errors.value = null
      }

      return isValid
    },
    submitHandler () {
      if (this.formIsValid()) {
        console.group('Form data')
        console.log('Type:', this.type)
        console.log('Value:', this.value)
        console.groupEnd()
      }
    }
  }
}
</script>
