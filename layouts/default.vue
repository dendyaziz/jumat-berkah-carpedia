<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="success">
      <b-navbar-brand href="/">Carpedia</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item to="/jual-mobil">Jual Mobil</b-nav-item>
        </b-navbar-nav>

        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-nav-form>
            <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
            <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
          </b-nav-form>

          <b-nav-item-dropdown v-if="$auth.loggedIn" right>
            <!-- Using 'button-content' slot -->
            <template #button-content>
              <em>{{ $auth.user.name }}</em>
            </template>
            <b-dropdown-item to="/iklan-saya">Iklan Saya</b-dropdown-item>
            <b-dropdown-item @click="$auth.logout()">Keluar</b-dropdown-item>
          </b-nav-item-dropdown>
          <b-nav-item v-else>
            <b-button size="sm" variant="danger" to="/login">Login</b-button>
            <b-button size="sm" variant="dark" to="/daftar">Register</b-button>
          </b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>

    <b-container>
      <Nuxt />
    </b-container>
  </div>
</template>

<script>

</script>

<style>

</style>
