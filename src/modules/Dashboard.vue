<template>
  <div id="card">
    <center>
      <b-card no-body class="overflow-hidden" style="max-width: 540px;">
        <center>
          <b-card-img id="image" :src="require('assets/user.png')" class="rounded-0"></b-card-img>
          <b-row no-gutters>
            <b-card-body>
              <h1>HI {{username}}</h1>
              <h3>Welcome to iTour</h3>
            </b-card-body>
          </b-row>
        </center>
      </b-card>
    </center>
  </div>
</template>

<style scoped lang="scss">
@import "assets/colors.scss";
#card {
  // margin-left: $margin-left !important;
  margin-top: $margin-top !important;
}
// .jumbotron {
//   padding: $padding !important;
//   text-align: $text-align !important;
//   color: $primary !important;
// }
#image {
  width: $width !important;
}
</style>

<script>
export default {
  name: "card",
  data() {
    return {
      username: sessionStorage.getItem("Username")
    };
  }
};
</script>

