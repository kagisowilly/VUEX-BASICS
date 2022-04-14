<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">

    <div class="counder-squared">
     {{$store.state.counter}}
     <sup>2</sup> = 
      {{$store.getters.counterSquared}}

    </div>
    <div class="buttons">
      <button @click="$store.dispatch('decreaseCounter')">-</button>
      <button @click="$store.dispatch('increaseCounter')">+</button>
    </div>
    <div>
      <input v-model="colorCode" type="text" placeholder="Enter color code">
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'HomeView',
  computed:{
    colorCode:{
      get(){
        return this.$store.state.colorCode
      },
      set(newValue){
        this.$store.dispatch('setColorCode', newValue)
      }
    }
  },
components:{
  'counter': require('@/components/Counter.vue').default
}
}
</script>

<style scoped>
div{
  margin-bottom: 10px;
}
.counter{
  font-size: 80px;
}
.buttons button {
  font-size: 40px;
  width: 100px;
  margin: 0 10px;
}
</style>
