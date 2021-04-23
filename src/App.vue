<template>
  <div class="roudaum-form">
    <b-card class="ml-4">
      <b-card-text>
        <b-form @submit="quandoSubmeter" @reset="quandoResetar">
          <b-form-group
              id="input-group-1"
              label="Nome do produto"
              label-for="input-1"
          >
            <b-form-input
                id="input-1"
                type="text"
                placeholder="Digite o nome do produto"
                required
            ></b-form-input>
          </b-form-group>

          <b-form-group id="input-group-2" label="Quantidade:" label-for="input-2">
            <b-form-input
                id="input-2"
                placeholder="Insira a quantidade"
                required
            ></b-form-input>
          </b-form-group>

          <b-button type="submit" variant="primary">Salvar</b-button>
          <b-button type="reset" variant="danger">Cancelar</b-button>
        </b-form>
        <b-card class="mt-3" header="Verificação do two-way-data-binding">
          <pre class="m-0">{{ produto }}</pre>
        </b-card>
      </b-card-text>
      <b-card-actions>
        <b-table
            :items="produtos"
            :fields="colunas"
            select-mode="single"
            responsive="sm"
            ref="selectableTable"
            selectable
            @row-selected="quandoSelecionaLinha"
        >
          <!-- Example scoped slot for select state illustrative purposes -->
          <template #cell(selected)="{ rowSelected }">
            <template v-if="rowSelected">
              <span aria-hidden="true">&check;</span>
              <span class="sr-only">Selecionado</span>
            </template>
            <template v-else>
              <span aria-hidden="true">&nbsp;</span>
              <span class="sr-only">Não selecionado</span>
            </template>
          </template>
        </b-table>
      </b-card-actions>
    </b-card>


  </div>
</template>

<script>
export default {
  data() {
    return {
      produtoSelecionado: {},
      produto: {
        nome: '',
        quantidade: '',
      },
      produtos: [{
        nome: 'Macarrão',
        quantidade: '3'
      }],
      colunas: ['nome', 'quantidade']
    }
  },
  methods: {
    quandoSubmeter(event) {
      event.preventDefault()
      alert(JSON.stringify(this.form))
    },
    quandoResetar(event) {
      event.preventDefault()
      // Reset our form values
      this.form.email = ''
      this.form.name = ''
      this.form.food = null
      this.form.checked = []
      // Trick to reset/clear native browser form validation state
      this.show = false
      this.$nextTick(() => {
        this.show = true
      })
    },
    quandoSelecionaLinha(items) {
      console.log(items)
    },

  }
}
</script>
