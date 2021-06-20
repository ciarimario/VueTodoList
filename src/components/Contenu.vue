<template>
    <Header />
    <main class="container">
        <TodoList />
        
    </main>
</template>

<script>
import Header from './Header.vue'
import TodoList from './TodoList.vue'


    export default {
        name:'Contenu',
        
        components:{
            Header,
            TodoList
            
        },
        
    }
</script>

<style lang="css" scoped>


</style>