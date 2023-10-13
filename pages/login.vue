<template>
  <div>
    <h1>Login</h1>

    <b-form @submit.prevent="login">
      <b-form-group
        label="Email:"
      >
        <b-form-input
          v-model="email"
          type="email"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group
        label="Password:"
      >
        <b-form-input
          v-model="password"
          type="password"
          required
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Login</b-button>
    </b-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    login() {
      this.$axios.post('http://localhost:8000/v1/login', {
        email: this.email,
        password: this.password,
      })
        .then(response => {
          this.$auth.setUserToken(response.data.token)
          this.getUser()
        })
    },
    getUser() {
      this.$axios.get('http://localhost:8000/v1/me')
        .then(response => {
          this.$auth.setUser(response.data.data)
          this.$router.push('/')
        })
    }
  }
}
</script>

<style>

</style>
