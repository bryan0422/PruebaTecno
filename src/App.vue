<template>
    <div>
    <div>
      
<img id="portada" src="https://techfactory.mx/wp-content/uploads/2019/09/Header-Techfactory.png">
</div>
  <b-table responsive striped hover :items="todos"></b-table>
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
  width: 100%;
  height: auto;
  background: black;  

}
</style>
