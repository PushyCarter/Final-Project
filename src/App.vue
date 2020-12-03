<!--
  Name: Michael Carter
  File: App.vue
  Description: Imported Header and Input to pull that data from the other vue files.
-->
<template>
  <div id="app" style="background-color: #000">
    <Header title="Check The Weather" />
    <Input />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Input from './components/Input.vue';

export default {
  name: 'App',
  components: {
    Header,
    Input,
  },
}
</script>

<style>
  *{
    margin: 0px;
    padding: 0px;
  }
</style>
