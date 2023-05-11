<template>
  <div>
    <div> 
      <input v-model="email" type="text" placeholder="email"/>
      <span :class="validEmail ? 'valid': 'error'"> Valid: {{ validEmail }} </span>
    </div>

    <div> 
      <input type="number" v-model="minAmount" placeholder="Min amount 10"/>
      <span :class="validMinAmount ? 'valid': 'error'"> Valid: {{ validMinAmount }} </span>
    </div>

    <div> 
      <input type="number" v-model="maxAmount" placeholder="Max amount 100"/>
      <span :class="validMaxAmount ? 'valid': 'error'"> Valid: {{ validMaxAmount }} </span>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const email = ref(null);
const minAmount = ref(null);
const maxAmount = ref(null);

const AMOUNT_MAP = {
  MIN: 10,
  MAX: 100
}

const validEmail = computed(() => email.value && /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(email.value))

const validMinAmount = computed(() => minAmount.value && minAmount.value >= AMOUNT_MAP.MIN);

const validMaxAmount = computed(() => maxAmount.value && maxAmount.value <= AMOUNT_MAP.MAX);

</script>

<style lang="scss">

</style>
