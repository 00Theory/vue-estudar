<!-- Options() API -->
<script>
export default {
  data() {
    return {
      name: 'João Ninguém',
      estado: 'pending',
      tarefas: ['t1, t2, t3'],
      link: 'https://google.com'
    };
  },
  methods: {
    toggleStatus() {
      if (this.estado === 'active') {
        this.estado = 'pending';
      }
      else if (this.estado === 'pending') {
        this.estado = 'inactive';
      }
      else {
        this.estado = 'active';
      }
    }
  }
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