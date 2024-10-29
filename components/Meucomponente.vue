<template>
  <div class="container">
    <h1>Cadastro de Times de Futebol</h1>

    <form @submit.prevent="adicionarTime" class="form-container">
      <div class="form-group">
        <label for="nomeTime">Nome do Time:</label>
        <input type="text" v-model="novoTime.nome" required>
      </div>

      <div class="form-group">
        <label for="paisOrigem">País de Origem:</label>
        <input type="text" v-model="novoTime.pais" required>
      </div>

      <div class="form-group">
        <label for="titulos">Número de Títulos:</label>
        <input type="number" v-model="novoTime.titulos" required>
      </div>

      <button type="submit" class="btn-submit">Cadastrar Time</button>
    </form>

    <h2>Lista de Times</h2>
    <table>
      <thead>
        <tr>
          <th>Nome do Time</th>
          <th>País de Origem</th>
          <th>Número de Títulos</th>
          <th>Ações</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(time, index) in times" :key="index">
          <td>{{ time.nome }}</td>
          <td>{{ time.pais }}</td>
          <td>{{ time.titulos }}</td>
          <td>
            <button @click="removerTime(index)" class="btn-remove">Remover</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      novoTime: {
        nome: '',
        pais: '',
        titulos: ''
      },
      times: []
    };
  },
  methods: {
    adicionarTime() {
      if (this.novoTime.nome && this.novoTime.pais && this.novoTime.titulos) {
        this.times.push({ ...this.novoTime });
        this.limparFormulario();
      }
    },
    removerTime(index) {
      this.times.splice(index, 1);
    },
    limparFormulario() {
      this.novoTime.nome = '';
      this.novoTime.pais = '';
      this.novoTime.titulos = '';
    }
  }
};
</script>

<style scoped>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #2c3e50;
  color: #666666;
}

.container {
  max-width: 800px;
  margin: 50px auto;
  padding: 20px;
  background-color: #34495e;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

h1, h2 {
  text-align: center;
  color: #ecf0f1;
}

.form-container {
  display: flex;
  flex-direction: column;
  gap: 15px;
  margin-bottom: 30px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

label {
  font-weight: bold;
  color: #bdc3c7;
}

input {
  padding: 10px;
  border: none;
  border-radius: 5px;
  background-color: #ecf0f1;
  color: #2c3e50;
}

input:focus {
  outline: none;
  box-shadow: 0 0 5px rgba(255, 255, 255, 0.5);
}

.btn-submit {
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  background-color: #27ae60;
  color: white;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn-submit:hover {
  background-color: #2ecc71;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}

thead {
  background-color: #2980b9;
}

th, td {
  padding: 12px;
  text-align: center;
  border-bottom: 1px solid #ecf0f1;
}

tbody tr:nth-child(odd) {
  background-color: #3b5998;
}

tbody tr:nth-child(even) {
  background-color: #2c3e50;
}

th {
  color: #fff;
}

td {
  color: #bdc3c7;
}

.btn-remove {
  padding: 5px 10px;
  background-color: #e74c3c;
  border: none;
  border-radius: 5px;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn-remove:hover {
  background-color: #c0392b;
}
</style>
