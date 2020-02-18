<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div> -->
    <router-view />
  </div>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}
html,
body {
  height: 100%;
  position: relative;
  -webkit-text-size-adjust: none;
}
#app {
  width: 100%;
  max-width: 750px;
  margin: auto;
  background-color: #ffffff;
  transform-origin: 0 0;
  overflow-x: hidden;
  position: relative;
  z-index: 1;
  display: block;
}
</style>
