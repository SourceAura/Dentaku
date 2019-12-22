<template>
  <div id="app">
    <div id="nav">
      <router-link to="/"
        ><vs-icon icon="home" size="small" color="#FFF"></vs-icon
      ></router-link>
      <div></div>

      <a href="https://github.com/SourceAura/vue-calc">
        <vs-icon icon="code" size="small" color="#FFF"></vs-icon
      ></a>

      <div></div>
      <router-link to="/about">
        <vs-icon icon="info" size="small" color="#FFF"></vs-icon
      ></router-link>
    </div>
    <router-view />
  </div>
</template>

<style lang="css">
@import url("https://fonts.googleapis.com/css?family=Titillium+Web&display=swap");

#app {
  font-family: "Titillium Web", sans-serif;
}
#nav {
  position: fixed;
  display: block;
  right: 0;
  bottom: 0;
  margin-right: 40px;
  margin-bottom: 40px;
  z-index: 900;
}

body {
  background: #100a1c;
  background-image: radial-gradient(
      50% 30% ellipse at center top,
      #201e40 0%,
      rgba(0, 0, 0, 0) 100%
    ),
    radial-gradient(60% 50% ellipse at center bottom, #261226 0%, #100a1c 100%);
  background-attachment: fixed;
  color: #6cacc5;
}
</style>
