<template>
  <div id="app">
    <Header></Header>
    <Sidebar id="side"
    v-show="$route.path === '/Dashboard' || $route.path === '/Subjects' || $route.path === '/PersonalInfo' || $route.path === '/Update'? true : false"></Sidebar>
    <AppBody></AppBody>
  </div>
</template>
<style scoped lang="scss">
@import "assets/colors.scss";
#app{
  background-image: $background-image !important;
  size: $size !important;
  background-repeat: $backgroud-repeat !important;
  overflow: $overflow !important;
  height: $height !important;
  max-height: $max-height !important;
}
#side{
  margin-top: 55px;
  padding-bottom: 50px;
}
</style>
<script>
import Header from "router/frame/Header.vue";
import AppBody from "router/frame/Body.vue";
import Sidebar from "router/frame/Sidebar.vue";
export default {
  name: "app",
  components: {
    Header,
    AppBody,
    Sidebar
  }
};
</script>


