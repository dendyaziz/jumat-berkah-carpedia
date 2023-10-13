<template>
  <div>
    <h1>Jual Mobil Anda</h1>
    <h3>Proses cepat, cepat untung!</h3>

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

      <b-button type="submit" variant="primary">Simpan dan Publish Iklan</b-button>
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
  methods: {
    save() {
      this.$axios.post('http://localhost:8000/v1/cars', {
        name: this.name,
        year: this.year,
        description: this.description,
      })
        .then(response => {
          this.$router.push('/')
        })
    },
  }
}
</script>

<style>

</style>
