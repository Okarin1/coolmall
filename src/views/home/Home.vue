<template>
  <div>
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <h1>Home</h1>
  </div>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar";
export default {
  name: "Home",
  components:{
    NavBar
  }
}
</script>

<style scoped>
.home-nav{
  background-color: var(--color-tint);
  color: white;
  font-size: large;
  font-weight: bold;
}
</style>
