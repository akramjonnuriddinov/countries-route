<template>
  <div id="app">
    <Header />
    <router-view></router-view>
  </div>
</template>

<script>
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style>
:root {
  --white: #fff;
  --shadow-color: #0000000E;
  --text-color: #111517;
  --gray: #848484;
  --border-color: #979797;
  --main-bg: #FAFAFA;
}

.dark-mode {
  --white: #2B3844;
  --shadow-color: rgba(0, 0, 0, 0.0562443);
  --text-color: #fff;
  --gray: #fff;
  --border-color: transparent;
  --main-bg: #202C36;
}

html {
  height: 100%;
  scroll-behavior: smooth;
  box-sizing: border-box;
}

*,
*::after,
*::before {
  box-sizing: inherit;
}

body {
  height: 100%;
  display: flex;
  flex-direction: column;
  margin: 0;
  padding: 0;
  color: var(--text-color);
  background-color: var(--white);
  font-family: "Nunito Sans", "Arial", sans-serif;
  font-weight: 400;
}

.container {
  max-width: 1320px;
  width: 100%;
  margin-left: auto;
  margin-right: auto;
  padding-left: 20px;
  padding-right: 20px;
}
</style>