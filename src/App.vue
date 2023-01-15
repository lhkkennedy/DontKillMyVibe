<template>
  <v-container>
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <router-view/>
  </v-container>
</template>

<style lang="scss">
 @import "./styles/mixins.scss";
 
#app {
 position: relative;
 padding: 0px auto;
 padding: 0px 2vw;
 z-index: 2;
 pointer-events: none;
}
 
#nav {
 padding: 30px;
 text-align: center;
 @include child-events-on();
 a {
   font-weight: bold;
   color: white;
 
   &.router-link-exact-active {
     color: blue;
   }
 }
}
</style>