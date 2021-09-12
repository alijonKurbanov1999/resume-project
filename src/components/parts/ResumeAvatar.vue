<template>
  <div class="avatar">
    <img :src="$attrs.value"><br>
    <small> Фото </small>
  </div>
</template>

<style scoped>
.avatar {
  display: block;
  text-align: center;


}
.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
