<template>
    <Additem v-on:add-task="AddTask"/>
   <div class="display">
       
        <div v-for="(item, index) in tasks" :key="index">
            <OneItem v-bind:task="item" v-on:mark-Completed="markDone" v-on:del-task="DeleteTask"/>
        </div>
    </div> 
</template>

<script>
import OneItem from './oneitem.vue';
import Additem from './additem.vue';
import axios from 'axios';
export default {
    name:"GetTasks",
    components:{
        OneItem,
        Additem,
    },
    data(){
        return{
            tasks:[]
        }
    },
    methods:{
         getData:function() {
             axios.get('http://localhost:3000/tasks')
             .then(response=>{
                 this.tasks=response.data;
                 })
             .catch(err=>console.log(err));
         },

        markDone(id){
            this.tasks[id-1].completed=!this.tasks[id-1].completed;
            axios.put(`http://localhost:3000/tasks/${id}`,this.tasks[id-1])
                .then(()=>this.getData)
                .catch(error=>console.log(error));
        },
        DeleteTask(id){
            this.tasks=this.tasks.filter(data=> data.id!==id);
            axios.delete(`http://localhost:3000/tasks/${id}`)
                .then(()=>this.getData)
                .catch(error=>console.log(error));
        },
        AddTask(newTask){
            this.tasks=[...this.tasks,newTask];
            axios.post('http://localhost:3000/tasks',newTask)
                .then(()=>this.getData())
                .catch(error=>console.log(error))
        }
    },
    beforeMount(){
       this.getData()
    }
}
</script>

<style scoped>

</style>