<template>
    <div class="singletask">
        <div class="flowleft">
            <input type="checkbox" v-on:change="$emit('mark-Completed',task.id)">
            <p v-bind:class="{'is-complete':task.completed}" class="tasktitle">{{task.task}}</p>
        </div>
        <i class="fa fa-trash" @click="$emit('del-task',task.id)"></i>
        <div class="clr"></div>
    </div>
</template>

<script>
export default {
    name:'OneItem',
    props: ['task'],
}
</script>

<style scoped>
    .clr{
        clear:both;
    }
    i{
        float: right;
    }
    .singletask{
            border: 2px solid aliceblue;
            margin: 10px;
            padding: 10px;
            height: auto;
    }
    input[type="checkbox"]{
        display: inline;
    }
    .tasktitle{
        display: inline;
        padding-left: 10px;
    }
    .flowleft{
        float: left;
    }
    .is-complete{
        text-decoration: line-through;
    }
</style>>