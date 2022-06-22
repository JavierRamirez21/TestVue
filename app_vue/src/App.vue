<template>
  <div id="app">
    <!-- <div class="container">
      <img class="centered" alt="Vue logo" src="./assets/logo.png" />
      <h1 class="title">Consultas de creditos</h1>
      <button class="button is-primary is-fullwidth" v-on:click="fetch">
        Consultar
      </button>
      <div class="columns">
        <div class="column">
          <table class="table is-bordered">
            <thead>
              <tr>
                <td>Num. Credito</td>
                <td>Cod. Tipo Credito</td>
                <td>Fecha Credito</td>
                <td>Fecha Ult. Movimiento</td>
                <td>Fecha pago final</td>
                <td>Cod. Asociado</td>
                <td>Nombre Asociado</td>
                <td>Saldo Capital</td>
                <td>Saldo Total Credito</td>
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
                <td>{{ c.totalApagarFecha }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div> -->
    <pm-lista-creditos></pm-lista-creditos>
  </div>
</template>

<script>
import PmListaCreditos from "./components/ListaCreditos.vue";

export default {
  name: "App",
  components: { PmListaCreditos },
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
