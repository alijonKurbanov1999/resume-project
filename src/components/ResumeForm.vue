<template>
  <form class="card card-w30" @submit.prevent="Send">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="type">
        <option value="title">Фамилия Имя Отчество</option>
        <option value="subtitle">Образование</option>
        <option value="avatar">Аватар</option>
        <option value="text">Профессиональный опыт</option>
      </select>
    </div>
    <br>
    <div class="form-control">
      <label for="value">Описание выбранного пункта:</label>
      <textarea id="value" rows="3" v-model="value"></textarea>
    </div>

    <button class="btn primary" :disabled="!invalid" :title="'Доступность кнопки, после заполения пунка описания!'">Добавить</button>
  </form>
</template>

<script>
export default {
  emits:['SEND'],
  data() {
    return {
      type: 'title',
      value: ''
    }
  },
  methods: {
    Send() {
      this.$emit('SEND', {
        type: this.type,
        value: this.value,
        id: Date.now()
      })
      this.type = 'title'
      this.value = ''
    }
  },
  computed: {
    invalid() {
      return this.value.length > 3
    }

  },
  name: "ResumeForm",
  components: {
  }
}
</script>

<style>
</style>
