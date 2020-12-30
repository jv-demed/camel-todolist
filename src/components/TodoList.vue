<template>
    <div class='todoList'>
        <NewTodo/>
        <List/>
    </div>
</template>

<script>
    import NewTodo from './NewTodo';
    import List from './List';
    export default{
        name: 'TodoList',
        components:{
            NewTodo,
            List
        }
    }
</script>

<style scoped>
    .todoList{
        align-items: center;
        background-color: #393e46;
        display: flex;
        flex-direction: column;
        min-height: 92vh;
    }
</style>