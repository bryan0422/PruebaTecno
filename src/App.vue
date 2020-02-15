<template>
<div class="frontcontainer">
  <img id="portada" src="https://techfactory.mx/wp-content/uploads/2019/09/Header-Techfactory.png">
  <b-table responsive dark striped hover :items="todos"></b-table>
    </div>
</template>

<script>
import axios from 'axios'

export default {
data(){
  return{
      todos:[]
  }
},
  mounted(){
      
      this.getTodos();
  },
  methods:{
  getTodos(){
      
      axios
      .get('https://www.proxtopic.com/facedetection/index.php/api/getDetection')
      .then( Response =>{
      this.todos = Response.data
    })
    .catch(e=> console.log(e))
  }
  }
}
</script>

<style>

#portada{
  display: block;
  width: 15%;
  margin-bottom: 5rem;
  margin-left: auto;
  margin-right: auto;
  margin-top: 5rem;
  height: auto; 
  
  
}
body{
  height: auto;
  margin: 0;
  padding: 0;
  width: 100%;
  background-color: black !important;
}
.frontcontainer{
  width: 100%;
  background: black; 
}
</style>
