<template>
  <Header />
  <h1>hello user you can add a restaurant</h1>
  <form class="add">
    <input type="text" name="name" v-model="restaurant.name" placeholder="Enter name" />
    <input type="text" name="adresse" v-model="restaurant.adresse" placeholder="Enter address" />
    <input type="text" name="contact" v-model="restaurant.contact" placeholder="Enter contact" />
    <button type="button" v-on:click="addRestaurant">Add new restaurant</button>
  </form>
</template>
<script>
import Header from "./Header.vue";
export default {
  name: "AddPage",
  data() {
    return {
      restaurant :{
        name:"",
      adresse:"",
      contact:""
      }
    }
  },
  methods: {
    addRestaurant(){
      console.warn(this.restaurant)
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
