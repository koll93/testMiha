<template>
  <div>
<!--    <select></select>-->
    <span @click="getValue">{{val}}</span>
  </div>
</template>

<script setup="props">

import {ref} from "vue";

const val = ref(23)

const getValue = () => {
  console.log(val)
}
</script>

<style scoped>

</style>
