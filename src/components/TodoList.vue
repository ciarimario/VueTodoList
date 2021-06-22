<template>
    <div>
        <section class='todo'>
           
            <form class="p-4 bg-dark">
                <div class="form-group inpuAddTask">
                    <!-- <label for="tache">Rentrer une tâche à faire</label> -->
                    <i class="fas fa-thumbtack"></i>
                    <input v-model.lazy="tache" id="tache" type="text" class="form-control" placeholder="Ajouter une tâche...">
                </div>
                <button v-on:click.prevent="ajoutItem" class="btn btn-outline-light mt-3 w-100">Ajouter la tâche</button>
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
    display: grid;
}
li {
    list-style-type: none;
    margin: 0;
    padding: 0;
}

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

</style>