<template>
    <v-card>
      <v-img :src="carData.image"></v-img>
      <v-card-title>{{ carData.title }}</v-card-title>
      <v-card-subtitle
        >Owner:
        <span class="font-weight-bold"
          >{{ carData.owner.lastName }} {{ carData.owner.firstName }}</span
        ></v-card-subtitle
      >
      <v-card-subtitle>
        Year: <span class="font-weight-bold"> {{ carData.yearOfMake }} <br /> </span> Miles:
        <span class="font-weight-bold">{{ carData.miles }}</span>
      </v-card-subtitle>
      <v-card-subtitle
        >Price: <span class="font-weight-bold">{{ carData.price }}</span></v-card-subtitle
      >
      <v-card-text>{{ carData.description }}</v-card-text>
      <v-card-actions>
        <v-btn @click="buyCarEvent()" color="red darken-2 white--text my-3">Buy Car</v-btn>
      </v-card-actions>
    </v-card>
</template>

<script>
export default {
  props: {
    carData: {
      type: Object,
      default: () => {},
    },
  },
  methods: {
    buyCarEvent() {
      this.$emit('BuyCar', this.carData);
    },
  },
};
</script>
