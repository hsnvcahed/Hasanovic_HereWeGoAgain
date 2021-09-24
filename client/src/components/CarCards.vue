<template>
  <v-row class="d-flex flex-wrap">
    <v-col style="width: 500px;" class="pa-15" v-for="(car, id) of carsData" :key="id">
      <CarCard @BuyCar="catchBuyCarEvent($event)" :carData="car"></CarCard>
    </v-col>
  </v-row>
</template>

<script>
import axios from 'axios';
import CarCard from '@/components/CarCard.vue';
export default {
  components: {
    CarCard,
  },
  props: {
    carsData: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    catchBuyCarEvent(event) {
      this.buyCar(event);
    },
    async buyCar(carData) {
      carData.title += ' RESERVED';
      await axios({
        method: 'PATCH',
        url: 'http://localhost:3000/cars/' + carData.id,
        'content-type': 'application/json',
        data: carData,
      });
    },
  },
};
</script>
