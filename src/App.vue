<template>
  <div id="app" class="has-text-centered">
    <img src="./assets/logo.png">
    <router-view class="container"/>
  </div>
</template>

<script>
export default {
  name: 'App',
};
</script>

<style>
  @import '../node_modules/bulma/css/bulma.css';
</style>
