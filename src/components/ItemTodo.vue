<template>
    <div class="todo">
        <div class="tache">{{ tache }}</div>
        <button v-on:click="suppressionTache" class="btn btn-danger">X</button>
    </div>
</template>

<script>
    export default {
        name:'ItemTodo',
        props:['tache','suppressionTache'],
    }
</script>

<style lang="css" scoped>
.todo {
    border:1px solid gray;
    border-radius: 5px;
    padding: 2em;
    margin: 1em;
    display:flex;
    justify-content: flex-start;
    align-items: center;
    position: relative;
}
.todo .tache {
    max-width:60%;
    
}
.todo button {
    position:absolute;
    right:20px;
}
</style>