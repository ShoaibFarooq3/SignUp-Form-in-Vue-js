<template>
  <div class="app">
    <div id="alert" v-if="alert">{{ alert }}</div>

    <div class="signup-container">
      <form @submit.prevent="submitForm">
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="formData.name">
  
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="formData.email">
        <label>
          Password
          <input type="password" v-model="formData.password" />
        </label>
        <label>
          Verify password
          <input type="password" v-model="formData.passwordVerify" />
        </label>
        <button type="submit">Submit</button>
      </form>
  
      <div v-if="formSubmitted">
        <h2>Form Submitted Successfully!</h2>
        <p>Name: {{ formData.name }}</p>
        <p>Email: {{ formData.email }}</p>
        <p>password: {{ formData.password }}</p>
      </div>
      
      <div v-if="formError">
        <p>Please fill out all fields.</p>
      </div>
      <!-- <form @submit.prevent="submitForm">
        <label>
          Email address
          <input type="email" v-model="email" />
        </label>
        <label>
          Account name (custom field)
          <input type="text" v-model="accountName" />
        </label>
        <label>
          Password
          <input type="password" v-model="password" />
        </label>
        <label>
          Verify password
          <input type="password" v-model="passwordVerify" />
        </label>
        <button type="submit">Sign up</button>
      </form>
      <div v-if="formError">
        <p>Please fill out all fields.</p>
      </div> -->
    </div>
  </div>
</template>

<script>
import Userfront from "@userfront/core";

// Initialize Userfront
Userfront.init("demo1234");

export default {
  data() {
    return {
      formData: {
        name: '',
        email: '',
        password:'',
        passwordVerify:''
      },
      formSubmitted: false,
      formError: false,
    };
  },
  methods: {
    submitForm() {
      if (
        this.formData.name.trim() === "" ||
        this.formData.password.trim() === "" ||
        this.formData.passwordVerify.trim() === "" ||
        this.formData.email.trim() === ""
      ) {
        this.formError = true;
        return;
      }

      // Reset error state
      this.formError = false;

      // Here you can handle form submission, for now just setting formSubmitted to true
      this.formSubmitted = true;
    },
  },
  // data() {
  //   return {
  //     email: "",
  //     accountName: "",
  //     password: "",
  //     passwordVerify: "",
  //     alert: "",
  //   };
  // },
  // methods: {
  //   // Sign up with the form's email and password
  //   signupWithPassword() {
  //     // Reset the alert to empty
  //     this.alert = "";
  //     // Verify that the passwords match
  //     if (this.password !== this.passwordVerify) {
  //       this.alert = "Passwords must match";
  //       return;
  //     }
  //     // Call Userfront.signup()
  //     Userfront.signup({
  //       method: "password",
  //       email: this.email,
  //       password: this.password,
  //       data: {
  //         accountName: this.accountName,
  //       },
  //     }).catch((error) => {
  //       this.alert = error.message;
  //     });
  //   },
  //   // Sign up with SSO (google)
  //   signupWithSSO() {
  //     Userfront.signup({ method: "google" });
  //   },
  // },
};
// export default {
//   name: 'HelloWorld',
//   props: {
//     msg: String
//   }
// }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button,
input {
  display: block;
  margin-bottom: 10px;
}

#alert {
  color: red;
  margin-bottom: 10px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.signup-container {
  max-width: 400px;

  margin: 0 auto;

  padding: 20px;

  border: 1px solid #ccc;

  border-radius: 8px;

  background-color: #fff;
}

h1 {
  font-size: 24px;

  margin-bottom: 20px;

  text-align: center;
}

form input {
  width: 100%;

  padding: 12px;

  margin-bottom: 10px;

  border-radius: 5px;

  border: 1px solid #ccc;

  box-sizing: border-box;
}

form button {
  background-color: #4caf50;

  color: white;

  border: none;

  cursor: pointer;

  width: 100%;

  padding: 12px;

  border-radius: 5px;
}

form button:hover {
  background-color: #45a049;
}
</style>
