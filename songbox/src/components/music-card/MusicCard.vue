<template>
  <div class="d-block card-music s-border-radius">
    <div class="img-card">
      <img class="img-fluid s-border-radius"  :src="useUploadFile(props.music.cover.url)" alt="capa do álbum">
    </div>
    <div class="d-flex justify-content-between text-card">
      <p class="text-truncate">{{ props.music.title }}</p>
    </div>
    <p class="artist-text text-truncate">{{ props.music.artist.name }}</p>
  </div>
</template>

<script lang="ts" setup>
import {useUploadFile} from "@/utils/useUploadURL";
import {Music} from "@/model/Music";

const props = defineProps({
  music: {
    type: Object as () => Music
  }
})

</script>
<style scoped>
.img-card {
  filter: drop-shadow(0px 0px 12px rgba(16, 16, 18, 0.5));
}

.text-card {
  margin-top: 0.8em;
  font-size: 1em;
  font-weight: 600;
  letter-spacing: 0.02em;
}

p {
  margin: 0;
}

.text-card > p {
  margin-bottom: 0.4em;
}

.card-music {
  background-color: var(--b-card-color);
  padding: 20px;
}

.artist-text {
  font-size: 0.8em;
  color: var(--b3-primary-color);

}
</style>