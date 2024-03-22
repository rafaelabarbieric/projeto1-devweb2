<script setup>

  import { ref } from 'vue'

  let usuario = ref({
    nome: '',
    sobrenome: '',
    email: '',
    dataNasc: '',
    endereco: '',
    cidade: '',
    estados: '',
    hobbies: [],
    lingProg: '',
    biografia: '',
    senha: '',
    sConfirmacao: ''
  })

  
  let estados = [
  {name: 'AC'},
  {name: 'AL'},
  {name: 'AP'}, 
  {name: 'AM'}, 
  {name: 'BA'}, 
  {name: 'CE'}, 
  {name: 'DF'},
  {name: 'ES'}, 
  {name: 'GO'}, 
  {name: 'MA'}, 
  {name: 'MT'}, 
  {name: 'MS'}, 
  {name: 'MG'}, 
  {name: 'PA'}, 
  {name: 'PB'}, 
  {name: 'PR'}, 
  {name: 'PE'}, 
  {name: 'PI'}, 
  {name: 'RJ'}, 
  {name: 'RN'},
  {name: 'RS'}, 
  {name: 'RO'}, 
  {name: 'RR'}, 
  {name: 'SC'}, 
  {name: 'SP'}, 
  {name: 'SE'},
  {name: 'TO'}
  ]

  const dadosUsuario = ref(true)

</script>

<template>

  <div v-if="dadosUsuario">
    <h1>Crie seu perfil:</h1>

    <form>

      <label for="nome">Nome:</label>
      <input type="text" id="nome" v-model="usuario.nome">

      <label for="sobrenome">Sobrenome:</label>
      <input type="text" id="sobrenome" v-model="usuario.sobrenome">

      <label for="email">Email:</label>
      <input type="email" id="email" v-model="usuario.email">

      <label for="dataN">Data de nascimento:</label>
      <input type="date" id="dataN" v-model="usuario.dataNasc">

      <label for="endereco">Seu endereço:</label>
      <input type="text" id="endereco" v-model="usuario.endereco">

      <label for="cidade">Sua Cidade:</label>
      <input type="text" id="cidade" v-model="usuario.cidade">

      <label for="estado">Informe seu estado:</label>
      <select id="estado" name="estados" v-model="usuario.estado">
        <option v-for="estado of estados" >{{ estado.name }}</option>
      </select>

      <label for="hobbies">Seus Hobbies:</label>
      <input type="checkbox" v-model="usuario.hobbies" value="esportes">Esportes
      <input type="checkbox" v-model="usuario.hobbies" value="musicas">Músicas
      <input type="checkbox" v-model="usuario.hobbies" value="filmes">Filmes
      <input type="checkbox" v-model="usuario.hobbies" value="viagens">Viagens
      <input type="checkbox" v-model="usuario.hobbies" value="leitura">Leitura

      <label for="lingProg">Sua Linguagem de Progamação Favorita:</label>
      <input type="radio" v-model="usuario.lingProg" value="C">C
      <input type="radio" v-model="usuario.lingProg" value="JavaSctipt">JavaScript
      <input type="radio" v-model="usuario.lingProg" value="Python">Python

      <label for="bio">Biografia:</label>
      <input type="text" id="bio" v-model="usuario.biografia">

      <label for="senha">Crie uma Senha:</label>
      <input type="text" id="senha" v-model="usuario.senha">

      <label for="senhaC">Confime sua Senha:</label>
      <input type="text" id="senhaC" v-model="usuario.sConfirmacao">

    </form>

    <button  @click="dadosUsuario = false">Enviar</button>

  </div>

  <div v-else>
    
    <h1>Seus Dados:</h1>

    <p>Nome: {{ usuario.nome }}</p>
    <p>Sobrenome: {{ usuario.sobrenome }}</p>
    <p>Email: {{ usuario.email }}</p>
    <p>Data de nascimento: {{ usuario.dataNasc }}</p>
    <p>Endereço: {{ usuario.endereco }}</p>
    <p>Cidade: {{ usuario.cidade }}</p>
    <p>Estado: {{ usuario.estado }}</p>
    <p>Hobbies: {{ usuario.hobbies.join(', ') }}</p>
    <p>Linguagem de Progamação favorita: {{ usuario.lingProg }}</p>
    <p>Bio: {{ usuario.biografia }}</p>
    <p>Senha: {{ usuario.senha }}</p>

    <button  @click="dadosUsuario = true">Editar</button>

  </div>
  
</template>

<style scoped>

</style>
