<template>
  <div class="container">
    <div class="card-image has-text-centered">
      <figure class="image is-64x64 is-inline-block">
        <img class="is-rounded" alt="Vue logo" src="../assets/logo.png" />
      </figure>
    </div>

    <h1 class="title has-text-centered">Consultas de creditos</h1>
    <div class="control">
      <input
        v-model="search"
        class="input is-rounded"
        type="text"
        name=""
        id=""
      />
      <button class="button is-primary" v-on:click="SearchData">
        Consultar por Usuario
      </button>
    </div>
    <button class="button is-primary is-fullwidth" v-on:click="fetch">
      Consulta General
    </button>
    <div class="columns">
      <div class="table-container">
        <table class="table is-bordered">
          <thead>
            <tr>
              <td>Num. Credito</td>
              <td>Cod. Tipo Credito</td>
              <td>Fecha Credito</td>
              <td>Fecha Ult. Movimiento</td>
              <td>Fecha pago Final</td>
              <td>Cod. Asociado</td>
              <td>Nombre Asociado</td>
              <td>Saldo Capital</td>
              <td>Saldo Total Credito</td>
              <td>Capital Mora</td>
              <td>Total Pagar</td>
            </tr>
          </thead>
          <tbody>
            <tr v-for="c of creditos" v-bind:key="c.id">
              <td>{{ c.creditoLinea.id }}</td>
              <td>{{ c.creditoLinea.codigo }}</td>
              <td>{{ c.fechaAlta }}</td>
              <td>{{ c.fechaUltPago }}</td>
              <td>{{ c.fechaPago }}</td>
              <td>{{ c.cliente.asociado }}</td>
              <td>{{ c.cliente.nombre }}</td>
              <td>{{ c.saldoCapital }}</td>
              <td>{{ c.saldoTotalCredito }}</td>
              <td>{{ c.capitalMora }}</td>
              <td>{{ c.totalApagarFecha }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      creditos: [],
      search: "",
    };
  },
  methods: {
    fetch() {
      let resultado = axios
        .get("https://planificadorapi.azurewebsites.net/api/Creditos/getList")
        .then((res) => {
          this.creditos = res.data;
          console.log(res.data);
        })
        .catch((err) => {
          console.log(err);
        });
    },
    SearchData() {
      const name = this.search;

      let resultados = axios
        .get(
          "https://planificadorapi.azurewebsites.net/api/Creditos/getListPorCliente/" +
            name +
            ""
        )
        .then((res) => {
          this.creditos = res.data;
          console.log(res.data);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>
<style lang="scss">
@import "@/scss/main.scss";
html {
  font-size: 14px;
}
button {
  margin-bottom: 20px;
}
</style>
