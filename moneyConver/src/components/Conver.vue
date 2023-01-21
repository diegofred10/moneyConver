<template>
  <h1>Conversor</h1>
    <div>
      <div>
        <div>
          <div>
            <div>
              <label for="cantidad">Ingrese Cantidad</label>
              <input
                type="number"
                id="cantidad"
                placeholder="Ingrese cantidad.."
                v-model="cantidad"
                v-on:keyup="onChange"
              />
            </div>
          </div>
        </div>
        <div>
          <div>
            <div>
              <label for="origin">Origen</label>
              <select
                id="origin"
                v-model="origin"
                v-on:change="onChange()"
              >
                <option v-for="(moneda, index) in monedas" v-bind:key="index">
                  {{ moneda }}
                </option>
              </select>
            </div>
          </div>
          <div>
            <div>
              <label for="exchange">Cambio</label>
              <select
                id="exchange"
                v-model="exchange"
                v-on:change="onChange()"
              >
                <option v-for="(moneda, index) in monedas" v-bind:key="index">
                  {{ moneda }}
                </option>
              </select>
            </div>
          </div>
        </div>
        <div>
          <h3 v-if="cantidad > 0">
            <span>{{ cantidad }} {{ origin }}</span>
            <span> SON </span>
            <span>{{ getTotal(total) }} {{ exchange }}</span>
          </h3>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        monedas: ["USD", "EUR", "LEM", "YEN"],
        cantidad: 0,
        origin: "USD",
        exchange: "EUR",
        total: 0,
      };
    },
    methods: {
      onChange() {
        switch (this.origin) {
          // Usuario selecciono que tiene dolares
          case "USD":
            if (this.exchange === "USD") {
              this.total = this.cantidad;
            }
            if (this.exchange === "EUR") {
              this.total = this.cantidad * 0.92;
            }
            if (this.exchange === "LEM") {
              this.total = this.cantidad * 24.67;
            }
            if (this.exchange === "YEN") {
              this.total = this.cantidad * 129.56;
            }
            break;
          // Usuario selecciono que tiene euros
          case "EUR":
            if (this.exchange === "USD") {
              this.total = this.cantidad * 1.09;
            }
            if (this.exchange === "EUR") {
              this.total = this.cantidad;
            }
            if (this.exchange === "LEM") {
              this.total = this.cantidad * 26.83;
            }
            if (this.exchange === "YEN") {
              this.total = this.cantidad * 140.92;
            }
            break;
            // Usuario selecciono lempiras
          case "LEM":
            if (this.exchange === "USD") {
              this.total = this.cantidad * 0.041;
            }
            if (this.exchange === "EUR") {
              this.total = this.cantidad * 0.037;
            }
            if (this.exchange === "LEM") {
              this.total = this.cantidad;
            }
            if (this.exchange === "YEN") {
              this.total = this.cantidad * 5.25;
            }
            break;
            // Usuario selecciono yenes
            case "YEN":
            if (this.exchange === "USD") {
              this.total = this.cantidad * 0.0077;
            }
            if (this.exchange === "EUR") {
              this.total = this.cantidad * 0.0071;
            }
            if (this.exchange === "LEM") {
              this.total = this.cantidad * 0.19;
            }
            if (this.exchange === "YEN") {
              this.total = this.cantidad;
            }
            break;
          default:
        }
      },
      getTotal(valor) {
          return Math.round(valor)
      }
    },
  };
  </script>
  
  <style scoped>
  .badge {
    margin: 2px;
    font-size: 150%;
  }
  label {
    font-weight: 700;
    font-size: 130%;
  }
  </style>