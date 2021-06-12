<template>
    <form class="my-form" @submit="addTask">
        <div class="form-group">
            <label>Add to the todo list</label>
            <input type="text" name="task" v-model="task">
            <button class="btn">ADD ITEM</button>
        </div>
    </form>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
    name:'Additem',
    data(){
        return{
            task:''
        }
    },
    methods:{
        addTask(e){
            e.preventDefault();
            const newTask={
                id:uuidv4,
                task:this.task,
                completed:false
            }
            this.$emit('add-task',newTask);
            this.task=''
        }
    }
}
</script>

<style scoped>
    .my-form{
        padding: 1em;
        /* line-height: 0.1em; */

    }

    .my-form input[type="text"]{
        padding:10px 15px;
        width:50%;
        border: none;
    }
    .btn{
        margin: 8px;
        background-color: #ff9e80;
        color: aliceblue;
        border: 2px solid aliceblue;
        padding:9px 15px;
    }
    label{
        display: block;
        font-size: 1em;
        letter-spacing:1px;
    }
</style>