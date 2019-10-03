<template>
  <div id="side">
    <!-- <div v-if="auth.user !== null">
      <Sidebar name ="side"></Sidebar>
      <transition>
        <router-view></router-view>
      </transition>
    </div>
    <div v-else> -->
      <transition>
        <router-view></router-view>
      </transition>
    </div>
  <!-- </div> -->
</template>

<style scoped>
</style>

<script>
// import AUTH from "services/auth";
// import Sidebar from "router/frame/Sidebar.vue";

// export default {
//   name: "side",
//   component: {
//     Sidebar
//   },
//   data() {
//     return {
//       auth: AUTH
//     };
//   }
// };
</script>

<style>
</style>

