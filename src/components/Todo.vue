<template>
    <div :id="'t'+todo.id" class='todo'>
        <form class='edit' v-if='edit.active' @submit.prevent='editTodo(index)'>
            <input type='text' v-model='edit.title' @blur='editTodo(index)'>
        </form>
        <div class='item' v-else>
            <div class="content">
                <input type='checkbox' :checked='todo.checked' @click="$emit('checkTodo', index)" />
                <div class='title'>
                    <span :alt='todo.title'>{{todo.title}}</span>
                </div>
            </div>
            <div class="infos">
                <Pencil class='pencil' @click='editMode' />
                <Trash class='trash' @click="$emit('removeTodo', index)" />
            </div>
        </div>
    </div>
</template>

<script>
    import Pencil from 'vue-material-design-icons/PencilOutline'
    import Trash from 'vue-material-design-icons/DeleteOutline';
    import '../assets/styles/icons.css';
    export default{
        name: 'Todo',
        props:{
            todo: Object,
            index: Number
        },
        components:{
            Pencil,
            Trash
        },
        data(){
            return{
                edit: {
                    title: this.todo.title,
                    active: false
                }
            }
        },
        methods:{
            editMode(){
                this.edit.active = true;
            },
            editTodo(i){
                this.$emit('editTodo', {
                    newTitle: this.edit.title,
                    index: i
                })
                this.edit.active = false;
            },
            editFocus(){
                let input = document.querySelector('.edit input');
                if(input != null){
                    input.focus();
                }
            },
        },
        updated(){
            this.editFocus();
        }
    }
</script>

<style scoped>
    .todo{
        border-bottom: 1px solid #706897;
        border-radius: 5%;
        height: 25px;
        padding: 0 5px;
        padding-top: 5px;
        padding-bottom: 2px;
    }
    .todo:hover{
        background-color:#3d424d; /* #393e46 */
    }
    .item{
        display: flex;
        justify-content: space-between;
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
        cursor: pointer;
    }
    input:checked ~ .title span{
        opacity: 0.7;
        text-decoration: line-through 2px;
    }
    .edit input{
        background-color: rgba(0, 0, 0, 0);
        border: none;
        color: #706897;
        width: 100%;
    }
</style>
