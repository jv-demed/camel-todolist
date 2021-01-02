<template>
    <div :id='todo.id' class='todo'>
        <div class="content">
            <input type='checkbox' :checked='todo.checked' @click="$emit('checkTodo', index)" />
            <div class='title'>
                <span :alt='todo.title'>{{todo.title}}</span>
            </div>
        </div>
        <div class="infos">
            <Trash class='trash' @click="$emit('removeTodo', index)" />
        </div>
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
        border-radius: 0 0 5% 5%;
        display: flex;
        height: 25px;
        justify-content: space-between;
        margin-bottom: 5px;
        padding: 0 5px;
    }
    .content{
        align-items: center;
        display: flex;
    }
    .title{
        margin: 0 6px;
    }
    .title span{
        margin: 0 2px;
    }
    input{
        color: #706897;
        cursor: pointer;
    }
    input:checked ~ .title span{
        opacity: 0.7;
        text-decoration: line-through 2px;
    }
</style>
