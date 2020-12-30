<template>
  <div id='App'>
    <Header/>
    <TodoList/>
  </div>
</template>

<script>
import Vue from 'vue';
import Header from './components/Header.vue';
import TodoList from './components/TodoList.vue';

export const eventBus = new Vue();

export default{
  name: 'App',
  components:{
    Header,
    TodoList
  }
}
</script>