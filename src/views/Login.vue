<template>
  
  <v-form>
    <div class="right-content">
      <v-form id="form" @submit.prevent="fromValidation">

        <div class="form-control">
          <label for="Email" class="heading">Email</label>
          <v-text-field type="text" id="email" v-model="email" />
          <span v-if="errorEmail" class="error">{{errorEmail}}</span>
        </div>

        <div class="form-control">
          <label for="password" class="heading">Password</label>
          <v-text-field v-model="password" type="password" id="password" />
          <span v-if="errorPassword" class="error">{{ errorPassword }}</span>
        </div>
        <!-- <v-btn type="submit">Signup</v-btn> -->
        <v-btn color="secondary" small type="submit">Login</v-btn>
      </v-form>
    </div>

  </v-form>
   
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
     
      email: "",
      password: "",
      errorEmail: "",
      errorPassword: "",
    }
  },
  methods : {
    fromValidation() {
      if (!/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(this.email)
      ) {
        this.errorEmail = "use @ and .com";
        return;
      }
      else if (this.email !== localStorage.getItem("email")) {
        this.errorEmail = "Email does not match";
        return;
      } else {
        this.errorEmail = "";
      }
      if (!/^(?=.*\d)(?=.*[a-z])(?=.*[A-Z])(?=.*[^a-zA-Z0-9])(?!.*\s).{8,20}$/.test(this.password)
      ) {
        this.errorPassword = "*** use 8-20 word one is Uppercase and LowerCase also Special Symbol  Password";
        return;
      }
      else if (this.password !== localStorage.getItem("password")) {
        this.errorPassword = "Password does not match";
        return;
      } else {
        this.errorPassword = "";
      }
      if(this.email && this.password){
        console.log("Login is Done");
        this.$router.push('DashBoard');
      }

    }
  }
  
}
</script>

<style>
.header {
  height: 28px;
  background-color: #2d3540;
  color: #fff;
  width: 100%;
}
.title {
  padding: 4px 3%;
  float: left;
}
.title_img {
  padding: 5px 3%;
  float: right;
}
div {
  display: block;
}
.n-footer {
  background: #043254 none repeat scroll 0 0;
  /* top:90%; */
  bottom: 0;
  position: fixed;
  width: 100%;
  text-align: center;
  padding: 10px 0;
}
#year1 {
  font-size: 1em;
  vertical-align: 0px;
}
.footer-content {
  display: inline-block;
  margin-right: 3%;
  margin-left: 2px;
}
.circle {
  background: #00aade none repeat scroll 0 0;
  border-radius: 50%;
  color: #ffffff;
  display: inline-block;
  font-size: 0.9em;
  width: 23px;
  height: 21px;
  padding-top: 2px;
}
.footer {
  color: #fff;
  font-size: 0.8em;
  font-weight: 600;
  float: left;
  margin-left: 3%;
  line-height: 23px;
}
.menu-items img {
  height: 100px;
  width: 250px;
}
.items {
  font-size: small;
  float: right;
  margin-right: 0%;
  margin-top: 25px;
  border-bottom: #00aade;
  border-width: 12px;
}
.right-content {
  color: white;
  background-color: rgb(125, 125, 254);
  display: inline;
  float: right;
  margin-right: 35%;
  margin-left: 60px;
  margin-bottom: 50px;
  padding: 10px 10px 10px 10px;
  border-radius: 32px;
  height: 350px;
  width: 370px;
}
.left-content {
  display: inline;
  float: left;

}
.left-content img {
  margin-left: 90px;
  
}
.right-content form a {
  font-size: small;
  float: right;
  margin-right: 30px;
  color: white;
  
}
.right-content form input {
  width: 90%;
  height: 20%;
  padding: 10px 10px 10px 10px;
  margin: 10px 10px 10px 10px;
  
}
.right-content form h1 {
  font-size: xx-large;
  font-weight: 600;
 
}
.right-content form .checkbx {
  float: left;
  font-size: small;
}
.right-content form {
  padding-left: 25px;
  padding-right: 25px;
  text-align: left;
}
.right-content form .btn1 {
  position: absolute;
  background-color: rgb(27, 192, 33);
  color: white;
  font-size: 16px;
  padding: 10px 20px;
  border: none;
  box-shadow: #2d3540;
  cursor: pointer;
  border-radius: 0px;
  align-items: center;
}
.right-content form .btn:hover {
  background-color: black;
}
.right-content form .checkbx {
  width: 10px;
}
.right-content .banner {
  background-color: white;
  width: 100%;
  height: 60px;
 
}
.n-footer .division {
  background-color: white;
  padding-top: 0 0 0 0;
  text-align: center;
  margin-top: 0%;
  color: orange;
  height: 60px;
  width: 100%;
  margin-top: 0px;
}
#radiobtn {
  width: 10px;
  height: 10px;
}
select {
  border-color: blue;
}
#phoneno {
  color: blue;
  font-weight: 800;
}
#redtext {
  color: red;
  font-weight: 800;
}
#best {
  color: blue;
  font-weight: 700;
}
#orange {
  color: orange;
  font-weight: 700;
}
#text-wrapper {
  margin-left: 120px;
  font-size: larger;
  font-weight: 600;
  width: 300px;
  height: 50px;
}
.error {
  color: red;
  font-size: 17px;
}
.heading {
  font-size: 22px;
  color: white;
}
.tb{
  text-align: center;
  border:1;
  margin-left: auto;
  margin-right: auto;
  margin-top: 20px;
}

</style>