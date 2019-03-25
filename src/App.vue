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
              <VTooltip bottom>
                <VBtn
                  color="primary"
                  outline
                  block
                  slot="activator"
                  @click="botao.funcao()"
                >
                  <VIcon>{{ botao.icon }}</VIcon>
                </VBtn>
                <span>{{ botao.label }}</span>
              </VTooltip>
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
        { icon: 'fas fa-plus', label: 'Somar', funcao: this.somar },
        { icon: 'fas fa-minus', label: 'Subtrair', funcao: this.subtrair },
        { icon: 'fas fa-times', label: 'Multiplicar', funcao: this.multiplicar },
        { icon: 'fas fa-divide', label: 'Dividir', funcao: this.dividir }
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
