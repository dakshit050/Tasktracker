<template>
  <div class="main">
    <link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <div class="title">
      <p class="heading">Todo List</p>
      <p>Get thing done, one item at a time</p>
    </div>
    <GetTasks />
  </div>
</template>

<script>
import GetTasks from './components/gettasks.vue';
export default {
  name: 'App',
  components: {
    GetTasks,
  }
}
</script>

<style>
#app {
  font-family: 'Open Sans', sans-serif;;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.main{
  left: 50%;
  top: 50%;
  position: absolute;
  transform: translate(-50%,-50%);
  width: 30%;  
  min-height: 63%;
  height: auto;
  background-color: #ff9e80  ;
  color: aliceblue;
}
.title{
  font-size: 0.7em;
  text-align: center;
  letter-spacing:1px;
  border-bottom: 1px solid aliceblue;
  line-height: 0.1em;

}
.heading{
  font-size: 35px;
}
@media(max-width:1024px) {
  .main{
  width: 89%;  
  min-height: 63%;
  }
}
</style>
