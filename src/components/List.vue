<template>
    <div class='list'>
        <Todo v-for='(todo, index) in list' 
            :key='todo.id' 
            :todo='todo' 
            :index='index'
            @checkTodo='checkTodo'
            @removeTodo='removeTodo'
            @editTodo='editTodo'/>
    </div>
</template>

<script>
    import {eventBus} from '../App';
    import Todo from './Todo';
    export default{
        name: 'List',
        components:{
            Todo
        },
        data(){
            return{
                list: JSON.parse(localStorage.getItem('camelTodo')) || [] 
            }
        },
        methods:{
            addTodo(todo){
                if(todo.title){
                    this.list.unshift(todo);
                }
            },
            removeTodo(i){
                this.list.splice(i, 1);
            },
            checkTodo(i){
                if(this.list[i].checked){
                    this.list[i].checked = false;
                }else{
                    this.list[i].checked = true;
                }
                this.save();
            },
            editTodo(obj){
                this.list[obj.index].id = Date.now();
                this.list[obj.index].title = obj.newTitle;
                this.save();
            },
            save(){
                localStorage.setItem('camelTodo', JSON.stringify(this.list));
            }
        },
        mounted(){
            eventBus.$on('addTodo', (todo)=> this.addTodo(todo));
        },
        updated(){
            this.save()
        }
    }
</script>

<style scoped>
    .list{
        margin: 30px 0;
        width: 550px;
    }
    @media(max-width: 600px){
        .list{
            width: 90%;
        }
    }
</style>
