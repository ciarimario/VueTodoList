<template>
    <div>
        <section class='todo mt-4'>
            <h1 class="text-center mb-3">Todo List</h1>
            <form>
                <div class="form-group">
                    <!-- <label for="tache">Rentrer une tâche à faire</label> -->
                    <input v-model.lazy="tache" id="tache" placeholder="Ajouter une nouvelle tâche..." type="text" class="form-control">
                </div>
                <button v-on:click.prevent="ajoutItem" class="btn btn-dark mt-3">Ajouter la tâche</button>
            </form>
            <h2 class="my-5">{{ titleTache }} ({{tableauTaches.length}})</h2>
            <ul>
                <li :key="index" v-for="(tache,index) in tableauTaches">
               <itemTodo :id="index" :tache="tache" :suppressionTache="supprTache" />
                </li>
            </ul>
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
}
li {
    list-style-type: none;
    margin: 0;
    padding: 0;
}
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
</style>