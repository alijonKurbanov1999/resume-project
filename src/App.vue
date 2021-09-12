<template>
  <div class="card center">
    <h1>RESUME.online </h1>
    <span>Сайт для создание резюме для поиска работы</span>
  </div>
  <div class="container column">
    <resume-form @SEND="Add"/>
    <resume-view :blocks="Blocks"/>
  </div>

  <div class="container">
    <resume-load v-if="loading"/>
    <resume-comments :comments="comments" @loading="Loading" v-else/>
  </div>
</template>

<script>
import ResumeForm from "./components/ResumeForm";
import ResumeView from "./components/ResumeView";
import ResumeComments from "./components/ResumeComments";
import ResumeLoad from "./components/ResumeLoad";
export default {
  data() {
    return {
      Blocks: [],
      comments: [],
      loading: false
    }
  },
  methods: {
    Add(block) {
      this.Blocks.push(block)
    },

    async Loading() {
      this.loading = true
      const res = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = await res.json()
      this.loading = false
    }
  },
  name: 'App',
  components: {ResumeForm, ResumeView, ResumeComments,ResumeLoad}
}
</script>

<style scoped>
 .card.center span {
   position: absolute;
   top: 90px;
   left: 38%;
   color: #2c3e50;
   font-family: cursive;
 }
</style>
