<template>
  <main class="container">
    <h1><strong>Avalie</strong> suas músicas favoritas, <strong>crie playlists</strong> e <strong>compartilhe</strong> sua opinião com todos </h1>
    <div class="d-flex justify-content-center">
      <button class="btn-song" @click="startNow">comece agora</button>
    </div>
  </main>
</template>

<script lang="ts" setup>
import router from "@/router";

function startNow() {
  router.push('/login')
}
</script>

<style scoped>
h1{
  text-align: center;
  font-weight: 700;
}
strong{
  color: #7882E0;
  font-weight: 700;
}

main > div{
  margin-top: 3em;
  padding-bottom: 3em;
}
</style>