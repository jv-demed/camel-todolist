<template>
    <div class='list'>
        <Todo v-for='(todo, index) in list' 
            :key='todo.id' 
            :todo='todo' 
            :index='index' 
            @removeTodo='removeTodo'/>
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
                if(todo){
                    this.list.unshift(todo);
                    this.save();
                }
            },
            removeTodo(i){
                this.list.splice(i, 1);
                this.save();
            },
            save(){
                localStorage.setItem('camelTodo', JSON.stringify(this.list));
            }
        },
        mounted(){
            eventBus.$on('addTodo', (todo)=> this.addTodo(todo));
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
