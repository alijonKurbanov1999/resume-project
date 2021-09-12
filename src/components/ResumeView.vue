
<template>
  <div class="card card-w70">
    <component v-if="blocks.length"
      v-for="block in blocks"
      :key="block.id"
      :is="'resume-'+ block.type"
      v-bind="{value: block.value}"
    >
    </component>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import ResumeTitle from "./parts/ResumeTitle";
import ResumeAvatar from "./parts/ResumeAvatar";
import ResumeSubtitle from "./parts/ResumeSubtitle";
import ResumeText from "./parts/ResumeText";
export default {
  props:['blocks'],
  name: "ResumeView",
  components: {ResumeTitle, ResumeAvatar, ResumeSubtitle, ResumeText}
}
</script>

<style scoped>

</style>
