<template>
<div class="frontcontainer">
  <b-img id="portada" center src="https://techfactory.mx/wp-content/uploads/2019/09/Header-Techfactory.png"></b-img>
  <!--<input placeholder="Buscar por nombre" type="text" @change="buscar" id="buscar">-->
    <div>
  <b-navbar type="light" variant="light">
    <b-nav-form>
      <b-form-input class="mr-sm-2" placeholder="Identity" @keyup="buscar" id="buscar"></b-form-input>
    </b-nav-form>
  </b-navbar>
</div>
  <b-table responsive dark striped hover :items="filterTodos"></b-table>
    </div>
</template>

<script>
import axios from 'axios'

export default {
data(){
  return{
      todos:[],
      filterTodos:[]
  }
},
  mounted(){
      
      this.getTodos();
  },
  methods:{
      buscar(e){
    console.log(e.target);
      if(!e.target.value.trim()){
        this.filterTodos = this.todos
        return
      } 

    let busqueda = e.target.value;
    this.filterTodos = this.todos.filter (i => i.identity.toLowerCase().includes(busqueda.toLowerCase()))
    //this.filterTodos = this.todos.filter(i=> i.identity.toLowerCase().trim() == busqueda.toLowerCase().trim())
    
  },
  getTodos(){
      
      axios
      .get('https://www.proxtopic.com/facedetection/index.php/api/getDetection')
      .then( Response =>{
      this.todos = Response.data
      this.filterTodos = this.todos

    })
    .catch(e=> console.log(e))
  }
  }
}
</script>

<style>

#portada{
  margin-bottom: 3rem;
  margin-top: 3rem;
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
