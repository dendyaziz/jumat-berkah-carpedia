<template>
  <div>
    <h1 class="mt-5 mb-4">Iklan Mobil Saya!</h1>

    <MyCarCard
      v-for="car in carList"
      :id="car.id"
      :image="car.image_url"
      :name="car.name"
      :year="car.year"
      :owner="car.owner_name"
      :description="car.description"
      @reload="getAllCar"
    ></MyCarCard>
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
      const response = await this.$axios.get('https://api-jumat.joyniso.com/v1/my-cars')
      this.carList = response.data.data
    }
  }
}
</script>

<style>

</style>
