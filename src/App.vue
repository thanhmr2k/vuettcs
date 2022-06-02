<template>
  <nav>
    <router-link to="/">Weather</router-link> |
    <router-link to="/about">Map</router-link> |
    <router-link to="/more">About</router-link>
  </nav>
  <transition
      mode="out-in"
      enter-active-class="animate__animated animate__fadeIn"
      leave-active-class="animate__animated animate__fadeOut"
    >
  <router-view />
  </transition>
</template>

<style>
*{
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
   background-image: linear-gradient(to top, rgba(102, 126, 234, 1), rgba(118, 75, 162, 1));
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
