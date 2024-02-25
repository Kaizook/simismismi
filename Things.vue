<template>
  <div>
    <h2>Lista de Ingredientes</h2>
    <div v-if="ingredientes">
      <h3>Massas:</h3>
      <ul>
        <li v-for="massa in ingredientes.massas" :key="massa.id">
          {{ massa.tipo }}
        </li>
      </ul>
      
      <h3>Sabores:</h3>
      <ul>
        <li v-for="sabor in ingredientes.sabores" :key="sabor.id">
          {{ sabor.tipo }}
        </li>
      </ul>
      
      <h3>Tamanhos:</h3>
      <ul>
        <li v-for="tamanho in ingredientes.tamanhos" :key="tamanho.id">
          {{ tamanho.tipo }}
        </li>
      </ul>
      
      <h3>Extras:</h3>
      <ul>
        <li v-for="extra in ingredientes.extras" :key="extra.id">
          {{ extra.tipo }}
        </li>
      </ul>
    </div>
    <div v-else>
      <p>Carregando...</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      ingredientes: null
    };
  },
  mounted() {
    this.fetchIngredientes();
  },
  methods: {
    async fetchIngredientes() {
      try {
        const response = await axios.get('http://localhost:3000/ingredientes');
        this.ingredientes = response.data;
      } catch (error) {
        console.error('Erro ao buscar ingredientes:', error);
      }
    }
  }
};
</script>

