<template>
    <div>
<<<<<<< HEAD
        <section class='todo mt-4'>
            <h1 class="text-center mb-3">Todo List</h1>
            <form>
                <div class="form-group">
                    <!-- <label for="tache">Rentrer une tâche à faire</label> -->
                    <input v-model.lazy="tache" id="tache" placeholder="Ajouter une nouvelle tâche..." type="text" class="form-control">
                </div>
                <button v-on:click.prevent="ajoutItem" class="btn btn-dark mt-3">Ajouter la tâche</button>
=======
        <section class='todo'>
           
            <form class="p-4 bg-dark">
                <div class="form-group inpuAddTask">
                    <!-- <label for="tache">Rentrer une tâche à faire</label> -->
                    <i class="fas fa-thumbtack"></i>
                    <input v-model.lazy="tache" id="tache" type="text" class="form-control" placeholder="Ajouter une tâche...">
                </div>
                <button v-on:click.prevent="ajoutItem" class="btn btn-outline-light mt-3 w-100">Ajouter la tâche</button>
>>>>>>> 9bd43c6f7858951c435a9681d7c06e665238dc97
            </form>
            <div class="container">
                <h3 class="my-5 text-center">{{ titleTache }} ({{tableauTaches.length}})</h3>
                <ul>
                    <li :key="index" v-for="(tache,index) in tableauTaches">
                        <itemTodo :id="index" :tache="tache" :suppressionTache="supprTache" />
                    </li>
                </ul>
            </div>
        </section>
    </div>
</template>

<script>
    import itemTodo from './ItemTodo.vue'
    
    export default {
        name:'TodoList',
        components:{
            itemTodo
        },
        data() {
            return {
                tache:'',
                tableauTaches:[],
                titleTache:'Vos tâches'
            }
        },
        methods:{
            supprTache:function(e) {
                this.tableauTaches.splice(e.target.parentNode.id,1)
                localStorage.setItem('items',JSON.stringify(this.tableauTaches))
                this.displayTitleTache()
            },
            ajoutItem:function() {
                this.tableauTaches.push(this.tache)
                this.tache=''
                const itemsArrayJson = JSON.stringify(this.tableauTaches)
                window.localStorage.setItem('items',itemsArrayJson)
                
                this.displayTitleTache()
            },
            displayTitleTache:function() {
                if(this.tableauTaches.length < 1) {
                    this.titleTache = 'Pas de taches'
                } else {this.titleTache = 'Vos taches'}
            }
        },
        mounted(){
            this.tableauTaches = JSON.parse(localStorage.getItem('items')) ? JSON.parse(localStorage.getItem('items')) : ['Pas de tache']
                
        }
    }
</script>

<style lang="css" scoped>
ul {
    margin: 0;
    padding: 0;
    display: grid;
}
li {
    list-style-type: none;
    margin: 0;
    padding: 0;
}
<<<<<<< HEAD
input[type="text"] {
    box-shadow: 0 2px 5px rgba(0,0,0,.2),0 0 5px rgba(0,0,0,.1);
    
    width:50%;
    margin-left: auto;
    margin-right:auto;
    padding:10px;
    border-radius: 10px;
    border:0;
}
input[type="text"]::placeholder {
    font-weight:bold;
    color:rgb(158, 155, 155);
    margin-left: 1em;
}
button {
    margin-left: auto;
    margin-right: auto;
    width:50%;
    display:block;
    border-radius: 10px;
    padding:10px;
}
=======

.inputAddTask {
    position: relative;

}
#tache {
    padding-left:50px;
}
#tache::placeholder {
   
    margin-left:auto;
    color:rgba(0,0,0,.3);
    
   
}



.inpuAddTask i.fa-thumbtack {
    color:rgba(0,0,0,.7);
    position: absolute;
    top:38px;
    left: 40px;
}

>>>>>>> 9bd43c6f7858951c435a9681d7c06e665238dc97
</style>