<template>
  <div class="hello">
    <form action="" method="post" role="form">
      <legend>Form Title</legend>

      <div class="form-group">
        <label>Nome</label>
        <input type="text" v-model="nome">
      </div>




      <button v-on:click.prevent="addAluno">Submit</button>
    </form>
    <table class="table table-hover">
      <thead>
      <tr>
        <th>nome</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="aluno in alunos">
        <td>{{ aluno.nome }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import firebase from 'firebase'
var firebaseApp = firebase.initializeApp({
  apiKey: "",
  authDomain: "",
  databaseURL: "",
  storageBucket: "",
  messagingSenderId: ""
})

var db = firebaseApp.database()

export default {
  name: 'hello',
  data () {
    return {
        nome: ''
    }
  },
  firebase: {
    alunos: db.ref('alunos'),
  },
  methods: {
      addAluno() {
          this.$firebaseRefs.alunos.push({
            nome: this.nome
          })
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
