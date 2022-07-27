<template>
  <router-view />

</template>

<script>



export default {
  name: 'App',
  components: {

}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
body{
  padding: 0;
  margin: 0;
}
.nav a {
    float: left;
    color: white;
    padding: 14px 16px;
    text-align: center;
    font-size: 18px;
    text-decoration: none;
    margin-right: 5px;
}
.nav a:hover{
  background-color: #ddd;
  color: #333;
}
</style>
