<template>
  <div id="app">
    <nav class='logo'>
      <router-link to='/'>
        <img alt="Pokemon logo" src="./assets/logo.svg">
      </router-link>
    </nav>
    <router-view/>
  </div>
</template>

<style lang="scss">
  * {
    box-sizing: border-box;
  }
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2C3E50;
  }
  .logo {
    width: min-content;
    margin: 0 auto;
  }

  .home {
    a {  
      text-decoration: none;
      color: #2C3E50
    }
  }
</style>
