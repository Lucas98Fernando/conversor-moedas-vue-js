<!-- Estrutura HTML do componente Conversor -->
<template>
  <div class="conversor">
    <div class="card">
      <h2 class="subtitulo">{{ moedaA }} para {{ moedaB }}</h2>
      <input
        class="valor-moeda"
        type="number"
        v-model="moedaA_value"
        v-bind:placeholder="moedaA"
      />
      <input
        class="btn-converter"
        value="Converter"
        type="button"
        v-on:click="converter"
      />
      <h2 class="resultado">{{ moedaB_value }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "Conversor",
  props: ["moedaA", "moedaB"],
  data() {
    return {
      moedaA_value: "",
      moedaB_value: 0,
    };
  },
  methods: {
    converter() {
      // Variável para receber os valores informados nos inputs
      let de_para = this.moedaA + "_" + this.moedaB;

      // API para pegar os valores atuais da moeda
      let url =
        "https://free.currconv.com/api/v7/convert?q=" +
        de_para +
        "&compact=ultra&apiKey=de3981bc53398825a7e1";

      fetch(url)
        .then((res) => {
          return res.json();
        })
        .then((json) => {
          let cotacao = json[de_para];
          this.moedaB_value = (cotacao * parseFloat(this.moedaA_value)).toFixed(
            2
          );
        });
    },
  },
};
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.card {
  max-width: 400px;
  padding: 20px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
}

.subtitulo {
  margin-bottom: 30px;
}

.resultado {
  margin-top: 20px;
}

.fa-coins {
  color: gold;
}

.valor-moeda {
  border-top-left-radius: 20px;
  border-bottom-left-radius: 20px;
  padding: 5px 15px;
  outline: none;
  font-family: "Poppins", sans-serif;
}

.btn-converter {
  border-top-right-radius: 20px;
  border-bottom-right-radius: 20px;
  padding: 5px 15px;
  outline: none;
  font-weight: 600;
  font-family: "Poppins", sans-serif;
  background: gold;
  color: #000;
  cursor: pointer;
}

.btn-converter:hover {
  box-shadow: 0px 0px 2px 2px #999;
}
</style>