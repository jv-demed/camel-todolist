<template>
    <header id='Header'>
        <img class='logo' src='../assets/images/logo.png' alt='Logo Camel To Do' />
    </header>
</template>

<script>
    export default{
        name: 'Header',
    }
</script>

<style scoped>
    header{
        align-items: center;
        background-color: #222831;
        display: flex;
        height: 8vh;
        justify-content: space-between;
        padding: 0 50px;
    }
    .logo{
        height: 6vh;
    }
    @media(max-width: 600px){
        header{
            justify-content: center;
        }
    }
</style>
