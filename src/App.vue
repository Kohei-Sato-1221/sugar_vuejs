<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/basic">Basic</router-link> | 
    <router-link to="/form">Form</router-link> | 
    <router-link to="/Css">CSS</router-link> | 
    <router-link to="/component">Component</router-link> | 
    <router-link to="/ope">Ope</router-link>
  </div>
  <router-view />
</template>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
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

.my-class {
  background-color: #42b983;
}
</style>
