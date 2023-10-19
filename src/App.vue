<script setup>

  import { reactive } from 'vue';

  const estado = reactive({
    operacao: '',
    a: 0,
    b: 0,
    resultado: 0 
  })

  const adicao = () => {
    return estado.resultado = estado.a + estado.b;
  }

  const subtracao = () => {
    return estado.resultado = estado.a - estado.b;
  }

  const multiplicacao = () => {
    return estado.resultado = estado.a * estado.b;
  }

  const divisao = () => {
    return estado.resultado = estado.a / estado.b;
  }

  const resolve = () => {
    const { operacao } = estado;

    switch(operacao) {
      case 'subtracao':
        return subtracao();
      case 'multiplicacao':
        return multiplicacao();
      case 'divisao':
        return divisao();
      default:
        return adicao();
    }
  }

  const atualizaA = (evento) => {
    estado.a = parseInt(evento.target.value);
    resolve();
  }

  const atualizaB = (evento) => {
    estado.b = parseInt(evento.target.value);
    resolve();
  }
</script>

<template>
  <div class="container">
    <header>
      <h1>Calculadora com Vue-JS</h1>
    </header>
    <main>
      <form>
        <label class="label-1" for="numero-1">Número 1:</label>
        <input @keyup="atualizaA" type="number" placeholder="Digite um número">
        <label class="label-2" for="numero-2">Número 2:</label>
        <input @keyup="atualizaB" type="number" placeholder="Digite um número">
        <label class="label-3" for="select">Selecione a operação aritmética:</label>
        <select @change="evento => estado.operacao = evento.target.value" name="escolha">
          <option value="adicao">Adição</option>
          <option value="subtracao">Subtração</option>
          <option value="multiplicacao">Multiplicação</option>
          <option value="divisao">Divisão</option>
        </select>
      </form>
      <div class="resultado">
        <p>
          O resultado é: {{ estado.resultado }}
        </p>
      </div>
    </main>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
}

.container {
  max-width: 960px;
  width: 100%;
  margin: 0 auto;
}

.container h1 {
  text-align: center;
}

main {
  max-width: 600px;
  margin: 0 auto;
  margin-top: 20%;
  font-size: 20px;
}

form {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

main input {
  padding: 8px;
  max-width: 300px;
}

.label-1 {
  margin-bottom: 8px;
}

.label-2 {
  margin-top: 16px;
  margin-bottom: 8px;
}
.label-3 {
  margin-top: 16px;
  margin-bottom: 8px;
}

select {
  max-width: 300px;
  padding: 8px;
}

p {
  margin-top: 16px;
}
</style>