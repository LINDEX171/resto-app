<template>
    <div class="nav">
    <a href="#">Home</a>
    <a href="#">Restaurant</a>
    <a href="#">Update</a>
    <a href="#" v-on:click="logout">Logout</a> 
    </div>
</template>
<script>
export default {
    name:"HeaderPage",
    methods: {
        logout(){
            // console.warn("logout")
            localStorage.clear();
            this.$router.push({name:'LoginPage'})
        }
    },
}
</script>
<style>
.nav{
    background-color: #333;
    overflow: hidden;
}
.nav a{
    float: left;
    color: #f2f2f2;
    padding: 14px 16px;
    text-align: center;
    font-size: 17px;
    text-decoration: none;
    margin-right: 5px;
}
.nav a:hover{
    background: #ddd;
    color: #333;
}
</style>