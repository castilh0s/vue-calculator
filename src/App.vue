<template>
  <div id="app">
    <h1>Calculadora Vue.Js</h1>

    <div>
      <input v-model="valorA" type="number" placeholder="Valor A">
      <input v-model="valorB" type="number" placeholder="Valor B">
    </div>

    <div>
      <button @click="somar()">+</button>
      <button @click="subtrair()">-</button>
      <button @click="multiplicar()">*</button>
      <button @click="dividir()">/</button>
    </div>

    <div v-if="resultado != null">
      <h3>
        Resultado: {{ resultado }}
      </h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',

  data() {
    return {
      valorA: null,
      valorB: null,
      resultado: null
    }
  },

  methods: {
    somar () {
      if (this.verificaValores()) {
        this.resultado = parseInt(this.valorA) + parseInt(this.valorB)
      }
    },
    subtrair () {
      if (this.verificaValores()) {
        this.resultado = parseInt(this.valorA) - parseInt(this.valorB)
      }
    },
    multiplicar () {
      if (this.verificaValores()) {
        this.resultado = parseInt(this.valorA) * parseInt(this.valorB)
      }
    },
    dividir () {
      if (this.verificaValores()) {
        this.resultado = parseInt(this.valorA) / parseInt(this.valorB)
      }
    },
    verificaValores () {
      if (this.valorA && this.valorB) {
        return true
      }

      return false
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

input, button {
  margin-left: 5px;
  margin-right: 5px;
}

div {
  margin: 10px;
}
</style>
