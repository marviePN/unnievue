<template>
  <div id="container">
    <center>
      <div id="card">
        <b-card no-body class="overflow-hidden" style="max-width: 540px;">
          <b-row no-gutters>
            <b-col md="6">
              <b-card-img :src="require('assets/user.png')" class="rounded-0"></b-card-img>
            </b-col>
            <b-col md="6">
              <b-card-body title="Personal Info">
                <hr>
                <b-card-text>
                  <h6>Username: {{username}}</h6>
                  <h6>Email: {{email}}</h6>
                  <h6 type="password">Password: {{password}}</h6>
                </b-card-text>
                <center>
                  <p>Do you want to edit your account?</p>
                  <router-link to="/Update">Edit</router-link>
                </center>
              </b-card-body>
            </b-col>
          </b-row>
        </b-card>
      </div>
    </center>
  </div>
</template>

<style scoped lang="scss">
@import "assets/colors.scss";
// .jumbotron{
//   color: $primary !important;
// }
#card {
  margin-top: 50px;
  // margin-left: 380px;
}
</style>
<script>
import AUTH from "services/auth";
export default {
  data() {
    return {
      auth: AUTH,
      username: sessionStorage.getItem("Username"),
      email: sessionStorage.getItem("Email"),
      password: sessionStorage.getItem("Password")
    };
  },
  methods: {
    update: function() {
      AUTH.update(this.username, this.email, this.password);
    }
  }
};
</script>
