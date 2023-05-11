<template>
  <div>
    <input v-model="email" type="text" placeholder="email"/>
    <span :class="validEmail ? 'valid': 'error'"> Valid: {{ validEmail }} </span>

    
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const email = ref(null);

const validEmail = computed(() => /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(email.value))

</script>

<style lang="scss">

</style>
