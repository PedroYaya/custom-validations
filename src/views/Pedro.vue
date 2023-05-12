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

    <div> 
      <input type="text" v-model="minChar" placeholder="Min char 10"/>
      <span :class="validMinChar ? 'valid': 'error'"> Valid: {{ validMinChar }} </span>
    </div>

    <div> 
      <input type="text" v-model="maxChar" placeholder="Max char 100"/>
      <span :class="validMaxChar ? 'valid': 'error'"> Valid: {{ validMaxChar }} </span>
    </div>


  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const email = ref(null);
const minAmount = ref(null);
const maxAmount = ref(null);
const minChar = ref(null);
const maxChar = ref(null);


const AMOUNT_MAP = { MIN: 10, MAX: 100 };

const CHAR_MAP = { MIN: 10, MAX: 100 };


const validEmail = computed(() => required(email.value) && validateEmail(email.value))

const validMinAmount = computed(() => required(minAmount.value) && validateMinAmount(minAmount.value, AMOUNT_MAP.MIN));

const validMaxAmount = computed(() => required(maxAmount.value) && validateMaxAmount(maxAmount.value, AMOUNT_MAP.MAX));

const validMinChar = computed(() => required(minChar.value) && validateMinChar(minChar.value, CHAR_MAP.MIN));

const validMaxChar = computed(() => required(maxChar.value) && validateMaxChar(maxChar.value, CHAR_MAP.MAX));

// VALIDATIONS

const required = val => !!val;

const validateEmail = email => typeof val === 'string' && /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(email);

const validateMinAmount = (val, min) => typeof val === 'number' && val >= min;

const validateMaxAmount = (val, max) => typeof val === 'number' && val <= max;

const validateMinChar = (val, min) => typeof val === 'string' && val.length >= min;

const validateMaxChar = (val, max) => typeof val === 'string' && val.length <= max;

</script>

<style lang="scss">

</style>
