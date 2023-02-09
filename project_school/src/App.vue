<template>
  <div id="app">
    <Alunos/>
  </div>
</template>

<script>
import Alunos from './components/Aluno/Alunos.vue';

export default {
  name: 'app',
  components: {
    Alunos
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,700");

body{
  background-color: #eee;
  font-family: "Montserrat", sans-serif;
  display: grid;
  justify-items: center;
}

body,html {
  margin: 0;
  height: 100%;
}

table{
   margin: 0px;
   padding: 0px;
   list-style-type: none;
   width: 100%;
}

table tr td {
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  margin-bottom: 2px;
  color: #3e5252;
}

table thead th{
  background-color: rgb(15, 85, 109) !important;
  font-size: 1.2em;
  padding: 10px 0px;
  text-align: center !important;
}

.colPequeno{
  width: 5%;
}

.btn_Danger{
  background-color: #fa4430;
}

.btn{
  cursor: pointer;
  border: 1px solid #000000;
  padding: 10px 20px;
  color: #FFFFFF;
  font-weight: bold;
  border-radius: 5px;
  border-bottom: 3px solid #000000;
}

.btn:hover{
  text-shadow: 1px 1px 1px black;
  margin-top: 3px;
  border-bottom: 1px solid black;
}

#app{

}
</style>
