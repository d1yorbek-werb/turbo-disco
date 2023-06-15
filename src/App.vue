<script setup>
  
import { ref } from 'vue';
import CHeader from './components/CHeader.vue';
import CLoginForm from './components/CLoginForm.vue';

defineProps({
  islogout: {
    type:Boolean,
    required:false,
    default: true
  }
})
const isAuthed = ref(false);

// onLogout  => isAuthed.value = false

const onLogin = (email, password) => {
  if (email == 'admin@domain.com' && password == 'pass') {
    isAuthed.value = true;
  } else {
    alert('parol yoki login xato!');
  }
}
</script>

<template>
  <div class="flex flex-col min-h-screen bg-gray-100">
    <CHeader :is-authed="isAuthed"></CHeader>
    <CLoginForm v-if="!isAuthed" @on-submitted="onLogin"></CLoginForm>
    <p class="text-center text-3xl text-green-700" v-else>welcome</p>
  </div>
</template>
<style>
  .logout {
  margin-left: 1000px;
  margin-top: -2px;
}
</style>