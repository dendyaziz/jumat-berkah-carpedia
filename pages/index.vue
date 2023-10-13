<template>
  <div>
    <h1 class="mt-5 mb-4">Yuk cari mobil favoritmu disini!</h1>

    <b-row>
      <b-col v-for="car in carList" md="6" xl="3">
        <CarCard
          :id="car.id"
          :image="car.image_url"
          :name="car.name"
          :year="car.year"
          :owner="car.owner_name"
          :description="car.description"
        ></CarCard>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      carList: []
    }
  },
  mounted() {
    this.getAllCar()
  },
  methods: {
    async getAllCar() {
      const response = await this.$axios.get('https://api-jumat.joyniso.com/v1/cars')
      this.carList = response.data.data
    }
  }
}
</script>

<style>

</style>
