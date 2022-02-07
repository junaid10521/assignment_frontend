<template>
  <div id="app">
    <h1 class="title">{{appName}}</h1>
  </div>
  <users-component />
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from 'vue';
import UsersComponent from './components/Users.vue';

export default defineComponent({
  name: 'App',
  components: {
    UsersComponent
  },
  setup(){
    const state = reactive({
      appName: 'UpWork Assignment' as string
    })

    return {...toRefs(state)}
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.title{
  color: #27ae60;
}
</style>
