<template>
    <div>
      <RandomNumber class="box" v-for="(number, index) in randomNumbers" :key="index" :initial-number="number" />
    </div>
  </template>
  
  <script>
  import RandomNumber from './RandomNumber.vue';
  
  export default {
    components: {
      RandomNumber
    },
    data() {
      return {
        randomNumbers: []
      };
    },
    mounted() {
      for (let i = 0; i < 100; i++) {
        this.randomNumbers.push(Math.floor(Math.random() * 100));
      }
      setInterval(this.updateRandomNumber, 1000);
    },
    methods: {
      updateRandomNumber() {
        const randomIndex = Math.floor(Math.random() * this.randomNumbers.length);
        this.$set(this.randomNumbers, randomIndex, Math.floor(Math.random() * 100));
      }
    }
  };
  </script>

<style scoped>
.box{
    display: flex;
    align-items: center;
}
</style>