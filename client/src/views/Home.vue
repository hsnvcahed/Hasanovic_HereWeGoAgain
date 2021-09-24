<template>
  <div>
    <LogoBar></LogoBar>
    <CarCards :carsData="carsData"></CarCards>
  </div>
</template>

<script>
import LogoBar from '@/components/LogoBar.vue';
import CarCards from '@/components/CarCards.vue';
import axios from 'axios';

export default {
  components: {
    LogoBar,
    CarCards,
  },
  data() {
    return {
      carsData: [],
    };
  },
  methods: {
    async getCars() {
      const result = await axios({
        method: 'GET',
        url: 'http://localhost:3000/cars',
      });
      this.carsData = result.data;
    },
  },
  created() {
    this.getCars();
  },
};
</script>
