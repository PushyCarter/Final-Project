<template>
  <div id="app">
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
    background: 'src/assets/Test.jpg'
  }
</style>
