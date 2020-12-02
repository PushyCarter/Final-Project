<template>
  <div id="app">
    <Header title="Check The Weather" />
    <Input />
    <Display />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Input from './components/Input.vue';
import Display from './components/Display.vue';

export default {
  name: 'App',
  components: {
    Header,
    Input,
    Display,
  },
}
</script>

<style>
  *{
    margin: 0px;
    padding: 0px;
  }
</style>
