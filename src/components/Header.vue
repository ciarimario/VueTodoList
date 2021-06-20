<template>
    <div>
        <header>
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
        min-height:200px;
        background: rgb(63, 62, 62);
        display:flex;
        justify-content: center;
        align-items: center;
    }

    header h2 {
        color:#fff;
    }

    
</style>