
<template>
  <div>
    <span>{{val}}</span>/
    <span>{{val2}}</span>
    <button @click="changeVal">click</button>

    <div style="margin: 20px">
      <select style="width: 200px" @change="changeSelect($event)">
        <option v-for="variant in selectOptions" :key="variant.id">{{variant.title}}</option>
      </select>
      <span style="margin-left: 30px">{{result}}</span>
    </div>
  </div>

  <hr>

  <div>
    <input v-model="inputVal" />
    <button @click="filterSelect">Фильтр меньше</button>
  </div>
</template>

<script setup="props">

const DEFAULT_COST = 50

import {ref} from "vue";

const val = ref(23)
let val2 = 2

const result = ref(null)

const inputVal = ref(null)

const selectOptions = ref([
  {
    id: 0,
    title: 'var1',
    value: 100
  },
  {
    id: 1,
    title: 'var2',
    value: 200
  },
  {
    id: 2,
    title: 'var3',
    value: 300
  }
])

const changeSelect = (e) => {
  result.value = selectOptions.value.find(v => v.title === e.target.value).value + DEFAULT_COST
  console.log('event', e.target.value)
}

const changeVal = () => {
  val.value += 1
  val2 += 1
}

const filterSelect = () => {
  const num = Number.parseInt(inputVal.value)
  if(num) {
    selectOptions.value = selectOptions.value.filter(v => v.value > num)
  } else {
    alert('Плохое значение')
  }
}
</script>

<style scoped>

</style>
