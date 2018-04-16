<template>
  <center><div class="column">
    <h1>K-Mart factory inventory</h1>
    <h2>Right here. Right now.</h2>
    <img src="/static/images/customer.jpg"/>
    <form v-on:submit.prevent="register">
      <p>Enter your current employee position.</p>
      <input class="narrow" v-model="username" placeholder="Position (i.e. manager, clerk etc.)">
      <p>Department and login information</p>
      <input class="wide" v-model="name" placeholder="Department"><br/>
      <input class="narrow" v-model="email" placeholder="Email Address">
      <input class="narrow" type="password" v-model="password" placeholder="Password">
      <button class="alternate" type="submit">Register</button>
    </form>
    <p class="error">{{registerError}}</p>
  <p>Food</p>
  <img class="front" src="/static/images/food.jpeg"/>
  <p>Lifestyle</p>
  <img class="front" src="/static/images/lifestyle.jpeg"/>
  <p>Electronics</p>
  <img class="front" src="/static/images/electronics.jpg"/>
  </div>
  </center>

</template>
<script>
 export default {
   name: 'WelcomePage',
   data () {
     return {
       username: '',
       email: '',
       password: '',
       name: '',
     }
   },
   computed: {
     registerError: function() {
       return this.$store.getters.registerError;
     },
   },
   methods: {
     register: function() {
       this.$store.dispatch('register',{
	 username: this.username,
         email: this.email,
         password: this.password,
	 name: this.name,
       });
     }
   }
 }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 100%;
 }
 .front {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 30%;
}
p {
  color: red;
}
 h1 {
     margin-bottom: 0px;
     color: red;
 }
 h2 {
     margin-top: 0px;
     font-size: 1.2em;
     font-weight: normal;
     margin-bottom: 50px;
     text-align: center;
     color: red;
 }
 .narrow {
     width: 170px;
 }
 .wide {
     width: 370px;
 }
</style>
