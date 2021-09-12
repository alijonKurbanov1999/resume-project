<template>
  <div class="card" v-if="comments.length">
    <h2>Комментарии</h2>
    <ul class="list">
      <li class="list-item" v-for="comment in comments">
        <div>
          <p><strong>{{comment.email}}</strong></p>
          <small>{{comment.body}}</small><hr/>
        </div>
      </li>
    </ul>
    <button class="btn danger" @click="comments.length = 0">Закрыть комментарии</button>
  </div>
  <p v-else>
    <button class="btn primary" @click="Loading" >Загрузить комментарии</button>
  </p>
</template>

<script>
export default {
  emits:['loading'],
  props: ['comments'],
  name: "ResumeComments",
  methods: {
    Loading() {
      this.flag = false
      this.$emit('loading')
    }
  }

}
</script>

<style scoped>

</style>
