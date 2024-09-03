<!-- Options() API -->
<script>
import { ref } from 'vue';
export default {
  setup() {
    const nome = ref('João Ninguém');
    const estado = ref('active');
    const tarefas = ref(['T1', 'T2', 'T3']);

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
    };

    return {
      nome,
      estado,
      tarefas,
      toggleStatus
    };
  },
};
</script>

<template>
  <h1>{{name}}</h1>
  <p v-if="estado === 'active'">User is active</p>
  <p v-else-if="estado == 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <h3>Tarefas:</h3>
  <ul>
    <li v-for="tarefa in tarefas" :key="tarefa"> {{ tarefa }}</li>
  </ul>
  <a :href="link">Clique para ir ao Google</a>
  <br />
  <!-- <button v-on:click="toggleStatus">Alterar Estado</button> -->
  <button @click="toggleStatus">Alterar Estado</button>
</template>