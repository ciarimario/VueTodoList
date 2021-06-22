<template>
   
    <main class="container-fluid m-0 p-0">
        <TodoList />
        
    </main>
    <MyFooter />
</template>

<script>

import TodoList from './TodoList.vue'
import Footer from './Footer.vue'


    export default {
        name:'Contenu',
        
        components:{
         
            TodoList,
            MyFooter:Footer
            
        },
        
    }
</script>

<style lang="css" scoped>


</style>