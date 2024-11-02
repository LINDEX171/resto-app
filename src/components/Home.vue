<template>
  <Header />
  <h1>Welcome {{ name }} to home componets</h1>
  <table border="1">
    <tr>
      <td>id</td>
      <td>name</td>
      <td>contact</td>
      <td>address</td>
      <td>actions</td>
    </tr>

    <tr v-for="item in restaurant" :key="item.id">
      <td>{{ item.id }}</td>
      <td>{{ item.name }}</td>
      <td>{{ item.contact }}</td>
      <td>{{ item.address }}</td>
      <td><router-link :to="'/update/'+item.id" >update</router-link></td>
    </tr>
  </table>
</template>
<script>
import Header from "./Header.vue";
import axios from "axios";
export default {
  name: "HomePage",
  data() {
    return {
      name: "",
      restaurant: [],
    };
  },
  components: {
    Header,
  },
  async mounted() {
    let user = localStorage.getItem("user-info");
    this.name = JSON.parse(user).name;
    if (!user) {
      this.$router.push({ name: "LoginPage" });
    }
    let result = await axios.get("http://localhost:3000/restaurant");
    console.warn(result);
    this.restaurant = result.data;
  },
};
</script>
<style>
td {
  width: 160px;
  height: 40px;
  
}
</style>