<template>
    <form class='newTodo'>
        <input type='text' placeholder='O que você precisa fazer?' v-model='newTodo'>
        <button @click.prevent='addTodo'>Add</button>
    </form>
</template>

<script>
    import {eventBus} from '../App';
    export default{
        name: 'NewTodo',
        data(){
            return{
                newTodo: ''
            }
        },
        methods:{
            addTodo(){
                let todo = {
                    id: Date.now(),
                    title: this.newTodo
                };
                eventBus.$emit('addTodo', todo);
                this.newTodo = '';
            }
        }
    }
</script>

<style scoped>
    .newTodo{
        display: flex;
        margin-top: 50px;
        width: 550px; /* 480 input, 50 button e 20 padding do input */
    }
    input, button{
        border: none;
        height: 30px;
        outline: none;
    }
    input{
        border-radius: 4px 0 0 4px;
        padding: 0 10px;
        width: 480px;
    }
    button{
        background-color: #706897;
        border-radius: 0 4px 4px 0;
        width: 50px
    }
    @media(max-width: 600px){
        .newTodo{
            width: 90%;
        }
        input, button{
            height: 50px;
        }
        input{
            width: 79.6%; /* 82.4% input, 15% button e 5.4% padding do input */
        }
        button{
            width: 15%;
        }
    }
    /* @media(max-width: 430px){
        .newTodo{
            display: flex;
        }
        input{
            width: 90%;
        }
        input{
            margin: 0 auto;
        }
    } */
</style>