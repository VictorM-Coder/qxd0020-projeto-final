<template>
  <div class="position-fixed container-fluid z-index-always-top" :class="{'bg-black': isOnTop}">
    <header class="container">
      <div class="d-flex row justify-content-between align-content-center">
        <div class="col-3 d-flex align-items-center">
          <router-link to="/">
            <i class="logo">
              <img src="@/assets/logo-songbox.svg" alt="logo  songbox">
            </i>
          </router-link>
        </div>

        <nav class="col-12 col-md-6 order-5 order-md-0 d-flex justify-content-center justify-content-md-end justify-content-lg-center mt-3 mt-md-0 border-sm-0 border-top">
          <ul class="nav">
            <li v-if="useUserStore().isAdmin" class="nav-item">
              <router-link class="nav-link" to="/admin" >Músicas</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/" >Home</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/reviews">Resenhas</router-link>
            </li>
          </ul>
        </nav>

        <div class="col-1 col-lg-3 d-flex justify-content-end align-items-center">
          <div class="d-flex align-items-center user-content">
            <span class="icon-user d-flex justify-content-center align-items-center me-2">
              <i class="bi bi-person"></i>
            </span>
            <div v-if="user.username" class="dropdown">
              <div class="dropdown-toggle"  id="dropdownMenuButton" data-bs-toggle="dropdown" aria-expanded="false">
                {{ user.username }}
              </div>
              <ul class="dropdown-menu bg-dark" aria-labelledby="dropdownMenuButton">
                <li><a @click="logout" class="dropdown-item text-white d-flex align-items-center" href="#">
                  <i class="bi bi-box-arrow-right me-3"></i>Sair
                </a></li>
              </ul>
            </div>
            <div v-else>
              <router-link to="/login">Entrar</router-link>
            </div>
          </div>
        </div>
      </div>
    </header>
  </div>
</template>

<script lang="ts" setup>
import {onBeforeUnmount, onMounted, ref} from "vue";
import {useUserStore} from "@/stores/userStore";

const user = ref(useUserStore().user)
const isOnTop = ref(false)

function handleScroll() {
  isOnTop.value = window.scrollY > 100;
}

function logout(){
  useUserStore().logout()
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
})

onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll);
})
</script>

<style scoped>
header {
  padding: 16px 0;
}
.z-index-always-top{
  z-index: 1020;
}
.logo:hover{
  cursor: pointer;
}

.bg-black {
  background-color: var(--b-primary-color);
  transition: background-color 0.2s ease-out;
}

.icon-user {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: var(--b2-primary-color);
}

.user-content {
  font-size: 1em;
  letter-spacing: 0.05em;
  color: var(--t1-primary-color);
  font-weight: 700;
}

@media (min-width: 576px) {
  .border-sm-0 {
    border: none !important;
  }
}
</style>
