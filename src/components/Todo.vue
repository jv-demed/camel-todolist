<template>
    <div :id='todo.id' class='todo'>
        <div>
            <input type='checkbox'>
            <span :alt='todo.title'>
                {{todo.title}}
            </span>
        </div>
        <Trash class='trash' @click="$emit('removeTodo', index)" />
    </div>
</template>

<script>
    import Trash from 'vue-material-design-icons/DeleteOutline';
    import '../assets/styles/icons.css';
    export default{
        name: 'Todo',
        props:{
            todo: Object,
            index: Number
        },
        components:{
            Trash
        }
    }
</script>

<style scoped>
    .todo{
        border-bottom: 1px solid #706897;
        /* border-radius: 0 0 0 5px; */
        display: flex;
        height: 25px;
        justify-content: space-between;
        margin-bottom: 5px;
        padding: 0 5px;
    }
    span{
        padding-left: 5px;
    }
</style>
