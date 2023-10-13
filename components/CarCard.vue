<template>
  <div>
    <b-card
      :title="name"
      :sub-title="year"
      :img-src="image"
      img-alt="Image"
      img-top
      tag="article"
      class="mb-2"
    >
      <b-card-text>
        {{ description }}
      </b-card-text>

      <b-card-text>
        Pemilik: {{ owner }}
      </b-card-text>

      <b-button href="#" variant="primary">Beli Sekarang</b-button>
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
    }
  }
</script>

<style scoped>

</style>
