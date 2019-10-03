<template>
  <div>
    <b-navbar toggleable="lg" variant="info">
      <center>
      <b-navbar-brand href="#" class="text text-light" id="title">iTour</b-navbar-brand></center>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
      <b-collapse id="nav-collapse" is-nav v-if="auth.user === null">
        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-navbar-nav>
            <b-nav-item v-show="$route.path === '/Login' || $route.path === '/Register' || $route.path === '/' ? true : false" @click="redirect('/Login')" class="text text-light" id="login">Login</b-nav-item>
            <b-nav-item v-show="$route.path === '/Login' || $route.path === '/Register' || $route.path === '/' ? true : false" @click="redirect('/Register')" class="text text-light" id="signup">Sign Up</b-nav-item>
          </b-navbar-nav>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>
<style scoped lang="scss">
@import "assets/colors.scss";
#title {
  color: $warning !important;
}

</style>
<script>
import ROUTER from "router"
import AUTH from 'services/auth'
export default {
  data(){
    return{
      auth: AUTH
    }
  },
  methods: {
    redirect(router) {
      ROUTER.push(router);
    }
  }
};
</script>
