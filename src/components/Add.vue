<template>
   <Header/>
  <h1>Welcome  to Add Restaurant componets</h1>
</template>
<script>
import Header from './Header.vue';
export default {
  name: "AddPage",
  components:{Header},
  mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name:'LoginPage'});
    }
  },
};
</script>
