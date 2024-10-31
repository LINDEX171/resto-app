<template>
    <img class="LOGO" src="../assets/resto.jpeg" alt="">
       <h1>Login</h1>   
       <div class="login" >
       <input type="email" v-model="email" placeholder="Enter Email" >
       <input type="text" v-model="password" placeholder="Enter Password" >
       <button >Login</button>
       <p>
       <router-link to="/sign-up">Sign Up</router-link>
       </p>
       </div> 
   </template>
   

<script>
export default {
    name : "LoginPage"

}
</script>