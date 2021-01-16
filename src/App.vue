<template>
  <div id="app">
    <h1 class="titulo-principal">
      Conversor de Moedas <img class="img-principal" src="./assets/coins.png" />
    </h1>
    <div class="divisor">
      <!-- Utilizando o componenete Conversor no arquivo principal da aplicação -->
      <Conversor moeda-a="USD" moeda-b="BRL" />
      <Conversor moeda-a="BRL" moeda-b="USD" />
    </div>
    <div class="divisor">
      <!-- Utilizando o componenete Conversor no arquivo principal da aplicação -->
      <Conversor moeda-a="CAD" moeda-b="BRL" />
      <Conversor moeda-a="BRL" moeda-b="CAD" />
    </div>
    <div class="divisor">
      <!-- Utilizando o componenete Conversor no arquivo principal da aplicação -->
      <Conversor moeda-a="EUR" moeda-b="BRL" />
      <Conversor moeda-a="BRL" moeda-b="EUR" />
    </div>
  </div>
</template>

<script>
// Importando o componente Conversor
import Conversor from "./components/Conversor";

export default {
  name: "App",
  components: {
    Conversor,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap");

body {
  font-family: "Poppins", sans-serif;
}

#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  max-width: 900px;
  margin: 50px auto;
}

.titulo-principal {
  display: flex;
  justify-content: center;
  align-items: center;
}

.img-principal {
  width: 60px;
  margin-left: 20px;
}

.divisor {
  display: flex;
  justify-content: space-around;
  margin-top: 30px;
}
</style>
