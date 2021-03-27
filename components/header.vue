<template>
  <div class="bg-light">
    <div class="container">
      <b-navbar toggleable="lg" type="light" variant="light">
        <b-navbar-brand href="/">Company-name</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav class="ml-auto">
            <b-nav-item
              href="/"
              :class="{'active': isHomeActive }"
              exact-active-class="active"
            >
              На Главную
            </b-nav-item>
            <b-nav-item
              href="/articles"
              :class="{'active': isArticlesActive }"
              exact-active-class="active"
            >
              Каталог статей
            </b-nav-item>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    isHomeActive: function() {
      if (this.$nuxt.$route.path=="/") {
        return true;
      } else {
        return false;
      }
    },
    isArticlesActive: function() {
      if (this.$nuxt.$route.path=="/articles" || this.$nuxt.$route.path == "/articles/:id") {
        return true;
      } else {
        return false;
      }
    },
  }
}
</script>
