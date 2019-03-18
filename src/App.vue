<template>
  <vApp>
    <vContainer
      grid-list-md
      text-xs-center
    >
      <VLayout wrap>
        <VFlex xs12>
          <h1>Calculadora Vue.Js</h1>
        </VFlex>

        <VFlex xs12>
          <input v-model="valorA" type="number" placeholder="Valor A">
          <input v-model="valorB" type="number" placeholder="Valor B">
        </VFlex>

        <VFlex xs12>
          <button @click="somar()">+</button>
          <button @click="subtrair()">-</button>
          <button @click="multiplicar()">*</button>
          <button @click="dividir()">/</button>
        </VFlex>

        <VFlex
          v-if="resultado != null"
          xs12
        >
          <h3>
            Resultado: {{ resultado }}
          </h3>
        </VFlex>
      </VLayout>
    </vContainer>
  </vApp>
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
