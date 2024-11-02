<template>
  <Header />
  <h1>hello user you can add a restaurant</h1>
  <form class="add">
    <input type="text" name="name" v-model="restaurant.name" placeholder="Enter name" />
    <input type="text" name="adresse" v-model="restaurant.address" placeholder="Enter address" />
    <input type="text" name="contact" v-model="restaurant.contact" placeholder="Enter contact" />
    <button type="button" v-on:click="addRestaurant">Add new restaurant</button>
  </form>
</template>
<script>
import Header from "./Header.vue";
import axios from "axios";
export default {
  name: "AddPage",
  data() {
    return {
      restaurant :{
        name:"",
      address:"",
      contact:""
      }
    }
  },
  methods: {
    async addRestaurant(){
      console.warn(this.restaurant)
      let result =await axios.post("http://localhost:3000/restaurant",{
        name:this.restaurant.name,
        address:this.restaurant.address,
        contact:this.restaurant.contact
      })
      if (result.status==201) {
        this.$router.push({ name: "HomePage" });
      }
      console.warn(result)
    }
  },
  components: { Header },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "LoginPage" });
    }
  },
};
</script>
