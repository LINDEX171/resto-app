<template>
 <img class="LOGO" src="../assets/resto.jpeg" alt="">
    <h1>Sign Up</h1>   
    <div class="register" >
    <input type="text" v-model="name" placeholder="Enter Name" >
    <input type="email" v-model="email" placeholder="Enter Email" >
    <input type="text" v-model="password" placeholder="Enter Password" >
    <button v-on:click="signUp">Sign Up</button>
    </div> 
</template>


<script>
import axios from 'axios';
export default {
    name : 'SignUp',
    data() {
        return {
            name:'',
            email:'',
            password:''

        }
    },
    methods: {
        async signUp()
        {
            //that will show the value of name,email,password of the user on console
            // console.warn("signup",this.name,this.email,this.password )
            let result = await axios.post("http://localhost:3000/users",{
                email:this.email,
                password:this.password,
                name:this.name
            })
            console.warn(result);
            if (result.status==201) {
              //  alert("signup done");
                localStorage.setItem("user-info",JSON.stringify(result.data))
                this.$router.push({name:'HomePage'})
            }

        }
    },
    mounted() {
        let user = localStorage.getItem("user-info")
        if(user){
            this.$router.push({name:'HomePage'})  
        }
    },
}
</script>

<style>
.logo{
    width: 100px;
}
.register input{
    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-right: auto;
    margin-left: auto;
    border: 1px solid skyblue;
}
.register button{
    width: 320px;
    height: 40px;
    border: 1px solid skyblue;
    background: skyblue;
    color: #fff;
    cursor: pointer;
}
</style>
