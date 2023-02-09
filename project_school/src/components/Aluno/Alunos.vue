<template>
    <div>
      <titulo texto="Aluno"/>
      <div>
      <input type="text" placeholder="Nome do Aluno" v-model="nome" @keyup.enter="addAluno()"/>
      <button class="btn btn_input" @click="addAluno()">Adicionar</button>
    </div>
  
      <table>
        <thead>
          <th>Mat.</th>
          <th>Nome</th>
          <th>Opções</th>
        </thead>
        <tbody v-if="alunos.length">
          <tr v-for="(aluno, index) in alunos" :key="index">
            <td>{{aluno.id}}</td>
            <td>{{aluno.nome}} {{aluno.sobrenome}}</td>
            <td>
              <button class="btn btn_Danger" @click="removerAluno(aluno)">Remover</button>
            </td>
          </tr>
        </tbody>
        <tfoot v-else>
          Nenhum aluno encontrado
        </tfoot>
      </table>
    </div>
  </template>
  
  <script>
import Titulo from '../_shared/Titulo';

  export default {
    components:{
        Titulo
    },

    data() {
      return {
        titulo: "Aluno",
        nome: "",
        alunos: [],
      };
    },
  
    created(){
      this.$http
      .get('http://localhost:3000/alunos')
      .then(res => res.json())
      .then(alunos => this.alunos = alunos)  
    },

    props: {},
  
    methods: {
      //esta função popula a varial aluno[]
      addAluno() {
        let _aluno = {
          nome: this.nome,
          sobrenome: ""
        }

      this.$http
      .post('http://localhost:3000/alunos', _aluno)
      .then(res => res.json())
      .then(aluno => {
         //this.nome recebe a variavel que vem do v-model no HTML
         this.alunos.push(aluno);
        this.nome = '';
      })
      },
  
      removerAluno(aluno){
  
      this.$http
      .delete(`http://localhost:3000/alunos/${aluno.id}`)
      .then(() => {
        let indice = this.alunos.indexOf(aluno);
        //informo a posição do aluno no array e removo o mesmo
        this.alunos.splice(indice, 1);
      })

     }
    },
  };
  </script>
  
  <style scoped>
  
    input{
      border: 0;
      padding: 20px;
      font-size: 1.3em;
      color: #687f7f;
      display: inline;
    }
  
  .btn_input{
    border: 0px;
    padding: 20px;
    font-size: 1.3em;
    display: inline;
    background-color: rgb(116,115,115);
  }
  
  .btn_input:hover{
    padding: 20px;
    margin: 0px;
    border: 0px;
  }
  </style>
  