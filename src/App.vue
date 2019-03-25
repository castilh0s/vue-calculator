<template>
  <VApp>
    <VContainer
      grid-list-md
      fill-height
    >
      <VLayout
        align-center
        justify-center
        text-xs-center
      >
        <VFlex xs12>
          <h1 class="display-2">
            Calculadora Vue.js
          </h1>

          <VLayout wrap>
            <VFlex xs12 md6>
              <VTextField
                v-model="valorA"
                label="Valor A"
              />
            </VFlex>
            <VFlex xs12 md6>
              <VTextField
                v-model="valorB"
                label="Valor B"
              />
            </VFlex>

            <VFlex
              v-for="botao in botoes"
              :key="botao.label"
            >
              <VBtn
                color="primary"
                outline
                block
                v-text="botao.label"
                @click="botao.funcao()"
              />
            </VFlex>
          </VLayout>

          <VDivider class="my-2" />

          <div
            v-if="resultado != null"
            class="headline"
          >
            Resposta: {{ resultado }}
          </div>
        </VFlex>
      </VLayout>
    </VContainer>
  </VApp>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      valorA: null,
      valorB: null,
      resultado: 0,
      botoes: [
        { label: 'Somar', funcao: this.somar },
        { label: 'Subtrair', funcao: this.subtrair },
        { label: 'Multiplicar', funcao: this.multiplicar },
        { label: 'Dividir', funcao: this.dividir }
      ]
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
  }
}
</script>
