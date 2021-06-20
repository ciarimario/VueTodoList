<template>
    <div>
        <section class='todo mt-4'>
            <h1>Todo List</h1>
            <form>
                <div class="form-group">
                    <label for="tache">Rentrer une tâche à faire</label>
                    <input v-model.lazy="tache" id="tache" type="text" class="form-control">
                </div>
                <button v-on:click.prevent="ajoutItem" class="btn btn-primary mt-3">Ajouter la tâche</button>
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
                tableauTaches:['Apprendre react','Apprendre Vue','Payer impôts'],
                titleTache:'Vos tâches'
            }
        },
        methods:{
            supprTache:function(e) {
                this.tableauTaches.splice(e.target.parentNode.id,1)
                this.displayTitleTache()
            },
            ajoutItem:function() {
                this.tableauTaches.push(this.tache)
                this.tache=''
                this.displayTitleTache()
            },
            displayTitleTache:function() {
                if(this.tableauTaches.length < 1) {
                    this.titleTache = 'Pas de taches'
                } else {this.titleTache = 'Vos taches'}
            }
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
</style>