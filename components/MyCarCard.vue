<template>
  <div>
    <b-card
      :title="name"
      :sub-title="year"
      :img-src="image"
      img-alt="Image"
      img-left
      tag="article"
      class="mb-2"
    >
      <b-card-text>
        {{ description }}
      </b-card-text>

      <b-card-text>
        Pemilik: {{ owner }}
      </b-card-text>

      <b-button href="#" variant="warning" :to="`/iklan-saya/${id}`">Ubah Iklan</b-button>
      <b-button href="#" variant="danger" @click="deleteCar">Hapus</b-button>
    </b-card>
  </div>
</template>

<script>
  export default {
    props: {
      id: Number,
      image: String,
      name: String,
      year: String,
      owner: String,
      description: String,
    },
    methods: {
      async deleteCar() {
        await this.$axios.delete(`https://api-jumat.joyniso.com/v1/cars/${this.id}`)
        await this.$emit('reload')
      }
    }
  }
</script>

<style scoped>

</style>
