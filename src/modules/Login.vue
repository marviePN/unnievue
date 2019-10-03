<template>
  <div id="background" style="padding-top:20px;">
    <center>
      <div id="divLogin" class="col-sm-3 my-sm-5 border rounded" style="margin-left:0.5%">
        <form class="container">
          <center>
            <h1>Login</h1>
          </center>
          <hr />
          <div class="row">
            <label id="username" for="loginUsername">Username:</label>
            <input
              required
              v-model="username"
              name="username"
              class="form-control"
              placeholder="Enter Username"
            />
            <br />
          </div>
          <br />
          <div class="row">
            <label id="pass" for="loginPassword">Password:</label>
            <input
              required
              v-model="password"
              type="password"
              name="password"
              class="form-control"
              id="loginPassword"
              placeholder="Enter Password"
            />
          </div>
          <br />
          <button id="btnLogin" class="btn btn-primary" @click="submit">
            <h6>Login</h6>
          </button>
          <br />
        </form>
      </div>
    </center>
  </div>
</template>
<style scoped lang="scss">
@import "assets/colors.scss";
h1 {
  color: $warning !important;
}
#username {
  color: $warning !important;
}
#pass {
  color: $warning !important;
}
</style>
<script>
import AUTH from "services/auth";
import ROUTER from "router";
import jquery from "jquery";
export default {
  data() {
    AUTH;
    return {
      username: "",
      password: ""
    };
  },
  methods: {
    submit: function(e) {
      e.preventDefault();
      let user = AUTH.login(this.username, this.password);
      if (this.username == "" || this.password == "") {
        this.$swal.fire(
          "Please provide inputs",
          "Inputs are required!",
          "warning"
        );
      } else {
        this.$swal.fire(
          "Please register first!",
          "You need to register!",
          "error"
        );
        AUTH.setUser(user);
        if (user !== null) {
          this.$swal.fire("Successfully Login!", "Nice one!", "success");
          ROUTER.push("/Dashboard");
        }
      }
      let link = `http://localhost:3000/db/create/$`;
      jquery.ajax({
          url: link,
          method: "GET",
          headers: {
            "Access-Control-Allow-Origin": "*"
          }
        })
        .then(response => {
          alert(response.username);
        });
    }
  }
};
</script>