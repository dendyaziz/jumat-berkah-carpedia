<template>
  <div>
    <h1>Ubah Iklan Anda</h1>

    <b-form @submit.prevent="save">
      <b-form-group
        label="Nama Mobil"
      >
        <b-form-input
          v-model="name"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group
        label="Tahun Pembelian"
      >
        <b-form-input
          v-model="year"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group
        label="Deskripsi"
      >
        <b-form-textarea
          v-model="description"
          required
        ></b-form-textarea>
      </b-form-group>

      <b-button type="submit" variant="primary">Simpan Iklan</b-button>
    </b-form>
  </div>
</template>

<script>
export default {
  middleware: ['auth'],
  data() {
    return {
      name: '',
      year: '',
      description: '',
    }
  },
  mounted() {
    this.getCar()
  },
  methods: {
    getCar() {
      this.$axios.get(`http://localhost:8000/v1/cars/${this.$route.params.id}`)
        .then(response => {
          const car = response.data.data
          this.name = car.name
          this.year = car.year
          this.description = car.description
        })
    },
    save() {
      this.$axios.put(`http://localhost:8000/v1/cars/${this.$route.params.id}`, {
        name: this.name,
        year: this.year,
        description: this.description,
      })
        .then(response => {
          this.$router.push('/iklan-saya')
        })
    },
  }
}
</script>

<style>

</style>
