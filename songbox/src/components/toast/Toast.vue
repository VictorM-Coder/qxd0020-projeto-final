<script setup lang="ts">
import { computed } from 'vue'
import {useNotificationStore} from "@/stores/useNotification";
import {Status} from "@/enums/Status";


const notificationStore = useNotificationStore()

const props = defineProps<{
  id: number
  message: string,
  status: Status
}>()

const isDark = computed(() => props.status !== Status.WARNING)

function remove() {
  notificationStore.dismiss(props.id)
}

</script>

<template>
  <div class="toast align-items-center border-0 show" :class="'text-bg-' + status" role="alert" aria-live="assertive" aria-atomic="true" data-bs-delay="300" data-bs-animation="true">
    <div class="d-flex">
      <div class="toast-body">
        {{ message }}
      </div>
      <button type="button" class="btn-close me-2 m-auto" :class="{'btn-close-white': isDark}" @click="remove" data-bs-dismiss="toast" aria-label="Close"></button>
    </div>
  </div>

</template>