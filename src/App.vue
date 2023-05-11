
<template>
  <div>
    <Alfred />
    <Pedro />
  </div>
</template>

<script setup>
  import Alfred from './views/Alfred.vue'
  import Pedro from './views/Pedro.vue'
</script>

<styles lang="scss">

div {
  font-weight: bold;
}

input {
  margin: 20px;
}

.error {
  color: red;
}

.valid {
  color: blue;
}

</styles>