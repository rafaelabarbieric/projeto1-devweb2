<script setup>

  import { reactive, ref } from 'vue'

  let usuario = reactive({
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
    sConfirmacao: '',
    fotoUsuario: null
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

  function handleFileUpload(e) {
    const target = e.target;
    if (target && target.files) {
      const file = target.files[0];
      usuario.fotoUsuario = URL.createObjectURL(file);
    }
  }

</script>

<template class="fundo">

  <!--Formulário-->
  <div class="form" v-if="dadosUsuario">
    <h1>Crie seu perfil:</h1>

    <!--Dados Pedidos-->
    <form>

      <div class="mb-3 mt-3">
        <label class="form-label" for="nome">Nome:</label>
        <input class="form-control" type="text" id="nome" v-model="usuario.nome">
      </div>projeto1-form-devweb2.surge.sh

      <div class="mb-3 mt-3">
        <label class="form-label" for="sobrenome">Sobrenome:</label>
        <input class="form-control" type="text" id="sobrenome" v-model="usuario.sobrenome">
      </div>

      <div class="mb-3 mt-3">
        <label class="form-label" for="email">Email:</label>
        <div class="input-group">
          <span class="input-group-text">@</span>
          <input class="form-control" type="email" id="email" v-model="usuario.email">
        </div>
      </div>
      

      <div  class="mb-3 mt-3">
        <label class="form-label" for="dataN">Data de nascimento:</label>
        <input class="form-control" type="date" id="dataN" v-model="usuario.dataNasc">
      </div>

      <div class="mb-3 mt-3">
        <label class="form-label" for="endereco">Seu endereço:</label>
        <input class="form-control" type="text" id="endereco" v-model="usuario.endereco">
      </div>

      <div class="mb-3 mt-3">
        <label class="form-label" for="cidade">Sua Cidade:</label>
        <input class="form-control" type="text" id="cidade" v-model="usuario.cidade">
      </div>

      <div class="mb-3 mt-3">
        <label class="form-label" for="estado">Informe seu estado:</label>
        <select class="form-select" id="estado" name="estados" v-model="usuario.estado">
          <option v-for="estado of estados " :key="estado" :value="estado.name">{{ estado.name }}</option>
        </select>
      </div>

      <div class="mb-3 mt-3">
        <label class="form-check" for="hobbies">Seus Hobbies:</label>
        <input class="form-check-input" type="checkbox" v-model="usuario.hobbies" value="esportes"> Esportes
        <input class="form-check-input" type="checkbox" v-model="usuario.hobbies" value="musicas"> Músicas
        <input class="form-check-input" type="checkbox" v-model="usuario.hobbies" value="filmes"> Filmes
        <input class="form-check-input" type="checkbox" v-model="usuario.hobbies" value="viagens"> Viagens
        <input class="form-check-input" type="checkbox" v-model="usuario.hobbies" value="leitura"> Leitura
      </div>

      <div class="mb-3 mt-3">
        <label class="form-check" for="lingProg">Sua Linguagem de Progamação Favorita:</label>
        <input class="form-check-input" type="radio" v-model="usuario.lingProg" value="C"> C
        <input class="form-check-input" type="radio" v-model="usuario.lingProg" value="JavaSctipt"> JavaScript
        <input class="form-check-input" type="radio" v-model="usuario.lingProg" value="Python"> Python
      </div>


      <div class="mb-3 mt-3">
        <label for="bio">Biografia:</label>
        <textarea class="form-control" rows="5" type="text" id="bio" v-model="usuario.biografia"></textarea>
      </div>

      <div class="mb-3 mt-3">
        <label class="form-label" for="senha">Crie uma Senha:</label>
        <input class="form-control" type="password" id="senha" v-model="usuario.senha">
      </div>

      <div class="mb-3 mt-3">
        <label class="form-label" for="senhaC">Confime sua Senha:</label>
        <input class="form-control" type="password" id="senhaC" v-model="usuario.sConfirmacao">
      </div>

      <!--Input Imagem-->
      <div class="mb-3 mt-3">
        <input class="form-control" type="file" id="fotoUsuario" @change="handleFileUpload($event)">
      </div>

    </form>

    <!--Botão Enviar-->
    <button v-if="usuario.senha === usuario.sConfirmacao" class="btn btn-primary" @click="dadosUsuario = false">Enviar</button>

  </div>


  <!--Dados do Usuario-->
  <div class="dados" v-else>
    
    <h2>Seus Dados:</h2>

    <!--Imagem-->
    <div id="img" class="mb-3 mt-3">
      <img class="imagem" v-if="usuario.fotoUsuario" :src="usuario.fotoUsuario">
    </div>

    <div class="mb-3 mt-3">
      <p>Nome: {{ usuario.nome }}</p>
    </div>

    <div class="mb-3 mt-3">
      <p>Sobrenome: {{ usuario.sobrenome }}</p>
    </div>

    <div class="mb-3 mt-3">
      <p>Email: {{ usuario.email }}</p>
    </div>

    <div class="mb-3 mt-3">
      <p>Data de nascimento: {{ usuario.dataNasc }}</p>
    </div>

    <div class="mb-3 mt-3">
      <p>Endereço: {{ usuario.endereco }}</p>
    </div>
    
    <div class="mb-3 mt-3">
      <p>Cidade: {{ usuario.cidade }}</p>
    </div>

    <div class="mb-3 mt-3">
      <p>Estado: {{ usuario.estado }}</p>
    </div>

    <div class="mb-3 mt-3">
      <p>Hobbies: {{ usuario.hobbies.join(', ') }}</p>
    </div>

    <div class="mb-3 mt-3">
      <p>Linguagem de Progamação favorita: {{ usuario.lingProg }}</p>
    </div>

    <div class="mb-3 mt-3">
      <p>Bio: {{ usuario.biografia }}</p>
    </div>

    <div class="mb-3 mt-3">
      <p>Senha: {{ usuario.senha }}</p>
    </div>

    <!--Botão Editar-->
    <button class="btn btn-primary"  @click="dadosUsuario = true">Editar</button>

  </div>
  
</template>

<style scoped>

/*Formulario*/
  .form{
    margin-top: 10%;
    margin-bottom: 10%;
    border: 1px solid rgb(223, 219, 219);
    border-radius: 6px;
    padding: 30px;
  }

  .form-check{
    margin-bottom: 10px;
  }
  .form-check-input{
    margin-left: 15px;
  }

/*Dados do Usuario*/
  .dados{
    margin-top: 10%;
    margin-bottom: 10%;
    border: 1px solid rgb(223, 219, 219);
    border-radius: 6px;
    padding: 50px;
  }

  h2{
    text-align: center
  }

/*Imagem*/
  .imagem{
    width: 200px;
    height: 200px;
    border-radius: 50%;
  }

  #img{
    text-align: center
  }

</style>
