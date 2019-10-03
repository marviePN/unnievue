<template>
  <center>
    <div
      data-toggle="collapse"
      id="divFrom"
      class="col-sm-3 my-sm-5 border rounded"
      style="margin-left:0.5%"
    >
      <form class="container">
        <center>
          <h1>Register</h1>
        </center>
        <hr />
        <div>
          <div class="row">
            <label id="username" for="inputfname">Username:</label>
            <input
              v-model="content.username"
              class="form-control"
              name="username"
              placeholder="Enter Username"
              required
            />
          </div>
          <br />
          <div class="row">
            <label id="email" for="inputEmail">Email:</label>
            <input
              required
              type="email"
              class="form-control"
              v-model="content.email"
              placeholder="Enter Email"
            />
          </div>
          <br />
          <div class="row">
            <label id="pass" for="inputPassword">Password:</label>
            <input
              required
              type="password"
              v-model="content.password"
              class="form-control"
              name="password"
              id="inputPassword4"
              placeholder="Password"
            />
            <br />
            <br />
          </div>
          <div class="row">
            <label id="conpass" for="inputConPassword">Confirm Password:</label>
            <input
              v-model="content.conpassword"
              required
              type="password"
              class="form-control"
              id="inputConPassword"
              placeholder="Confirm Password"
            />
            <span></span>
            <br />
            <br />
          </div>
        </div>
        <button id="btnSubmit" type="submit" class="btn btn-primary" @click="submit">
          <h6>Register</h6>
        </button>
        <br />
        <p>Already have an account?</p>
        <router-link to="/Login">Login</router-link>
        <br />
      </form>
    </div>
  </center>
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
#email {
  color: $warning !important;
}
#conpass {
  color: $warning !important;
}
p {
  color: $warning !important;
}
</style>
<script>
import AUTH from "services/auth";
import jquery from "jquery";
export default {
  data() {
    return {
      auth: AUTH,
      content: {
        username: "",
        email: "",
        password: "",
        conpassword: ""
      }
    };
  },
  methods: {
    submit: function(e) {
      e.preventDefault();
      sessionStorage.setItem("Username", this.content.username),
        sessionStorage.setItem("Email", this.content.email),
        sessionStorage.setItem("Password", this.content.password);
      if (
        this.content.username == "" ||
        this.content.email == "" ||
        this.content.password == "" ||
        this.content.conpassword == ""
      ) {
        this.$swal.fire(
          "Please provide inputs",
          "Inputs are required!",
          "warning"
        );
      } else if (this.content.password != this.content.conpassword) {
        this.$swal.fire("Password Mismatch!", "Type properly!", "error");
      } else {
        AUTH.register(
          this.content.username,
          this.content.password,
          this.content.email,
          this.content.conpassword
        );
        this.$swal.fire("You are registered!", "Nice one!", "success");
      }

      let link = `http://localhost:3000/db/create/${this.content.username}/ ${this.content.email}/${this.content.password}`;
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
