<template>
  <center><div class="column">
    <h1>Walmart factory inventory</h1>
    <h2>Save money. Live better. Walmart</h2>
    <img src="/static/images/customer.jpg"/>
    <form v-on:submit.prevent="register">
      <p>Enter your current employee ID.</p>
      <input class="narrow" v-model="username" placeholder="Eployee ID">
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
  <img class="front" src="/static/images/electronics.jpg"/><br><br>
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
  color: #007dc6;
}
 h1 {
     margin-bottom: 0px;
     color: #007dc6;
 }
 h2 {
     margin-top: 0px;
     font-size: 1.2em;
     font-weight: normal;
     margin-bottom: 50px;
     text-align: center;
     color: #007dc6;
 }
 .narrow {
     width: 170px;
 }
 .wide {
     width: 370px;
 }
</style>
