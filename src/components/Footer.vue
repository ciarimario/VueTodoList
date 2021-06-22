<template>
    <div>
        <footer class="bg-dark">
            <ul>
                <li><i class="fas fa-home"></i></li>
                <li><i class="fas fa-bookmark"></i></li>
                <li><i class="fas fa-search"></i></li>
            </ul>
        </footer>
    </div>
</template>

<script>
export default {
   name:'Footer'
}
</script>

<style scoped>
footer {
    height:50px;
    width:100%;
    color:#fff;
    position:fixed;
    bottom:0;
    
}
ul {
    margin: 0;
    padding: 0;
    display: flex;
    justify-content:center;
    align-items: center;
}
li {
    list-style-type: none;
    margin: 0;
    padding: 1em;
}
li i:hover {
    color:gray;
    cursor:pointer;
}

</style>