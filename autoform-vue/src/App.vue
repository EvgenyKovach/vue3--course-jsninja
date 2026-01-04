<script setup lang="ts">
import { ref } from 'vue';  
import AuthPage from './components/pages/AuthPage.vue';

const title = ref<string>('Авторизация');

</script>

<template>
  <div class="pp">
    <h2>Авторизация</h2>
    <AuthPage 
      :title="title"
    />
  </div>
</template>

<style>
.pp {
  display: flex;
  flex-direction: column;
}
</style>