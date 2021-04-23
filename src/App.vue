<template>
  <div class="roudaum-form">
    <b-card class="ml-4" header="Parte 1">
      <b-card-text >
        <b-card-title>Inclusão de um produto</b-card-title>
        <b-form>
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
      </b-card-text>
    </b-card>
      <b-card class="mt-3 ml-4" header="Parte 2">
        <b-card-title>Lista de Produtos</b-card-title>
        <b-card-sub-title>Verificação do one-way-data-binding</b-card-sub-title>
        <pre class="m-0">{{ produtoSelecionado }}</pre>
        <b-card-text>
          <div>
            <b-table
                :items="produtos"
                :fields="colunas"
                select-mode="single"
                responsive="sm"
                ref="selectableTable"
                selectable
                @row-selected="quandoSelecionaLinha"
            >
            </b-table>
          </div>
        </b-card-text>
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
    quandoSelecionaLinha() {

    },

  }
}
</script>
