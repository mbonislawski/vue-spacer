<template>
  <div class="app">
    <div id="nav">
      <router-link to="/">Spacer</router-link>
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,600,800');

  $font-weight-light: 300;
  $font-weight-normal: 400;
  $font-weight-bold: 600;
  $font-weight-black: 800;

 * {
   box-sizing: border-box;
 }

 body {
   margin: 0;
   padding: 0;
   font-family: 'Montserrat', sans-serif;
   color: #fff;
   -webkit-font-smoothing: antialiased;
   text-shadow: 1px 1px 1px rgba(0,0,0,0.004);
 }

.fade-enter-active, 
.fade-leave-active {
  transition: opacity .3s ease;
}

.fade-enter, 
.fade-leave-to
/* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

</style>
