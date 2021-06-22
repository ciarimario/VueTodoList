<template>
    <div>
        <header class="bg-dark">
            <h2>Welcome on my Todo List</h2>
        </header>
    </div>
</template>

<script>
    export default {
        name:'Header'
    }
</script>

<style lang="css" scoped>
    header {
        width:100%;
        min-height:50px;
        display:flex;
        justify-content: center;
        align-items: center;
    }

    header h2 {
        color:#fff;
    }

    
</style>