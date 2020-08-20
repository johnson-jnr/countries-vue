<template>
  <div id="app">
    <div id="nav" v-if="$route.name!='CountryDetail'">
      <router-link to="/">Home</router-link>|
      <router-link to="/about">About</router-link>
      <br />
    </div>
    <keep-alive include="Home">
      <router-view />
    </keep-alive>
  </div>
</template>

<style>
#app {
  box-sizing: border-box;
  padding: 20px 6% 6%;
  /* padding-bottom: 100px; */
}

#nav {
  margin-bottom: 20px;
  /* padding: 30px; */
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
