<script setup>

  import { ref } from 'vue'

  let usuario = ref({
    nome: '',
    sobrenome: '',
    email: '',
    dataNasc: '',
    endereco: '',
    estados: '',
    hobbies: '',
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

</script>

<template>

  <div>
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

      <label for="estado">Informe seu estado:</label>
      <select id="estado" name="estados" v-model="usuario.estados">
        <option v-for="estado of estados" >{{ estado.name }}</option>
      </select>

      
    </form>
  </div>
  
</template>

<style scoped>

</style>
