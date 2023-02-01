<template>
  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav> -->
  <router-view />
</template>

<style>
:root {
  --coral: #eb7e7f;
  --greeny: #4ebc9b;
  --lamppost: #4a4f56;
  --lamppostopacity: rgba(74, 79, 86, 0.25);

  --radius: 3px;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html,
body {
  font-size: 16px;
  height: 100%;
}

body {
  font-family: Trebuchet, Arial, sans-serif;
  background-color: #3b3f45;
  padding-bottom: 42px;
  position: relative;
}
</style>
