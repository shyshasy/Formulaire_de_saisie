<template>
  <div id="app">
    <UserForm />
  </div>
</template>

<script>
import UserForm from './components/UserForm.vue';

export default {
  name: 'App',
  components: {
    UserForm
  }
};
</script>

<style>
#app {
  font-family: 'Georgia', serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
  background-color: #f7f7f7;
}
</style>
