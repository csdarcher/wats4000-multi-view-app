<template>
  <div class="home">
    <div v-show="showForm" class="form-container">
      <h1>Join the Web Developers Club!</h1>
      <p>Sign up to access our special, secret page. Just create an account and answer a brief survey.</p>

      <p v-show="showError" class="error">There are some errors in the data that you answered! 
      Please take a look to ensure everything was entered correctly. All fields are required.</p>
      
      <form v-on:submit.prevent="validateForm">

        <p><label for="username">
          <input type ="text" id="username" v-model="username" placeholder="Enter your username here.">
        </label></p> 

        <p><label for="email">
          <input type ="email" id="email" v-model="email" placeholder="emailaddress@email.com">
        </label></p>  

        <p><label for="password">
          <input type ="password" id="password" v-model="password" placeholder="Enter your password here.">
        </label></p> 

        <p><label for="passwordVerify">
          <input type ="password" id="passwordVerify" v-model="passwordVerify" placeholder="Just to make sure we got, please enter your password again.">
        </label></p> 

        <p><input type="submit" value="Submit"></p>
      </form>
    </div>
    <div v-show="!showForm" class="success-message">
      <h1>Thank you for signing up!</h1>
      <p>Please take our new member survey. <router-link to="Survey">Click here</router-link></p><!-- TODO: Link "Click here" to the survey page. -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      username: '',
      email: '',
      password: '',
      passwordVerify: '',
      showForm: true,
      showError: false
    }
  },
  methods: {
    validateForm: function () {
      if ((this.username != '') &&
         (this.email != '') &&
         (this.password === this.passwordVerify)) {
        console.log('Form is valid.');
        this.showForm = false;    
         } else {
         console.log('Form NOT vaild!');
          this.showError = true;  

         }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  border: 3px solid #aa0000;
  padding: 1rem;
  color: #aa0000;
}
h1, h2 {
  font-weight: normal;
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
</style>
