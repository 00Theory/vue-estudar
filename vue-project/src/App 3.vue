<!-- Options() API -->
<script setup>
import { onMounted, ref } from 'vue';

const nome = ref('João Ninguém');
const estado = ref('active');
const tarefas = ref(['T1', 'T2', 'T3']);
const link = ref(['https://google.com']);

const toggleStatus = () => {
  if (estado.value === 'active') {
    estado.value = 'pending';
  }
  else if (estado.value === 'pending') {
    estado.value = 'inactive';
  }
  else {
    estado.value = 'active';
  }
}

const adicionarTarefa = () => {
  if (novaTarefa.value.trim() !== '')
  {
    tarefas.value.push(novaTarefa.value);
    novaTarefa.value = '';
  }
}

const deletarTarefa = (index) => {
  tarefas.value.splice(index, 1);
}

onMounted(async () => {
  try {
    const resposta = await fetch('https://jsonplaceholder.typicode.com/todos');
    const data = await resposta.json();
    tarefas.value = data.map((tarefa) => tarefa.title);
  } catch (error) {
    console.log('Error fetching tarefas');
  }
})

</script>

<template>
  <h1>{{name}}</h1>
  <p v-if="estado === 'active'">User is active</p>
  <p v-else-if="estado == 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <!-- FORMULÁRIO--> 
  <form @submit.prevent="adicionarTarefa">
    <label for="adicionarTarefa">Adicionar Tarefa</label>
    <br/>
    <input type="text" id="novaTarefa" name="novaTarefa" v-model="novaTarefa"/>
    <br/>
    <button type="submit">Enviar</button>
  </form>

  <h3>Tarefas:</h3>
  <ul>
    <li v-for="(tarefa, index) in tarefas" :key="tarefa">
      <span>
        {{ tarefa }}
        </span>
        <button @click="deletarTarefa()"> X </button>
      </li>
  </ul>
  <a :href="link">Clique para ir ao Google</a>
  <br />
  <!-- <button v-on:click="toggleStatus">Alterar Estado</button> -->
  <button @click="toggleStatus">Alterar Estado</button>
</template>