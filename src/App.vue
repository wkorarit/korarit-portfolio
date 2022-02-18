<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div> -->
    <router-view/>
  </div>
</template>
<script>
export default {
  beforeDestroy(){
    localStorage.removeItem("taskNumber")
    localStorage.removeItem("sunTask")
    localStorage.removeItem("monTask")
    localStorage.removeItem("tueTask")
    localStorage.removeItem("wedTask")
    localStorage.removeItem("thuTask")
    localStorage.removeItem("friTask")
    localStorage.removeItem("satTask")
  }

}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700;800&display=swap');
#app {
  font-family: 'Poppins', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #222831;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
