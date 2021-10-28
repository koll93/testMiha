<template>
  <input v-model="valInput"/>
  <button v-for="button in [1,2,3]" :key="button" @click="setNumber(button)">{{ button }}</button>
  <button v-for="button in ['+','-','=']" :key="button" @click="setNumber(button)">{{ button }}</button>

</template>


<script>

// import Counter from "./components/Counter.vue";
// import ToDo from "./components/ToDo.vue";

export default {
  components: {
    // Counter,
    // ToDo,
  },
  data: function () {
    return {
      valInput: ''
    }
  },
  methods: {
     setNumber: function (number2) {
       if (number2 === '=') {

         if (this.valInput.includes('+')) {
           const idx = this.valInput.indexOf('+')
           console.log(idx)
           this.valInput = +this.valInput.split('+')[0] + +this.valInput.split('+')[1]
         } else if (this.valInput.includes('-')) {
         //
         } else {
           console.log('HUY')
         }
       } else {
         this.valInput += number2
       }
     }
}
};
</script>
