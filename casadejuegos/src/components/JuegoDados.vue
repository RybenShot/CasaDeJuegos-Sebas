<template>
  <div class="app BGJuegos">
    <div class="container">
      <br />

      <!-- FORMULARIO -->
      <div class="formulario columns">
        <div class="column">
          <p>Numero de DADOS</p>
          <div>
            <button @click="NDeDados++" class="py-2 px-4 mr-3">+</button>
            <input type="number" v-model="NDeDados" class="py-2 px-2 px-2" />
            <button @click="NDeDados--" class="py-2 px-4 ml-3">-</button>
          </div>
          
        </div>

        <div class="column">
          <!-- <p>Numero de LADOS </p> -->
          <!-- <br> -->

          <div class="columns is-mobile">
            <div class="column">
              <p class="is-3"><i class="fas fa-dice"></i></p>
              <p>4 lados</p>
              <input type="radio" v-model="NDeLados" class="mx-2" id="cuatro" value= 4 />
            </div>
            <div class="column">
              <p><i class="fas fa-dice-d6"></i></p>
              <p>6 lados</p>
              <input type="radio" v-model="NDeLados" class="mx-2" id="seis" checked value= 6 />
            </div>
            <div class="column">
              <p><i class="fas fa-dice"></i></p>
              <p>8 lados</p>
              <input type="radio" v-model="NDeLados" class="mx-2" id="ocho" value= 8 />
            </div>
            <div class="column">
              <p><i class="fas fa-dice"></i></p>
              <p>12 lados</p>
              <input type="radio" v-model="NDeLados" class="mx-2" id="doce" value= 12 />
            </div>
            <div class="column">
              <p><i class="fas fa-dice-d20"></i></p>
              <p>20 lados</p>
              <input type="radio" v-model="NDeLados" class="mx-2" id="veinte" value= 20 />
            </div>
          </div>
        </div>
      </div>

      <!-- BOTOND DE LANZAR DADOS -->
      <!-- Aqui indicamos ya el minimo del resultado que debe salir y el maximo lo indicamos con "NDeLados" -->
      <div class="columns is-mobile">
        <button
          @click="tirarDados(1)"
          class="column button is-success is-active mx-5"
        >
          TIRAR!
        </button>
        <!-- <button
          @click="vaciarArray()"
          class="column button is-danger is-active mx-5"
        >
          Vaciar
        </button> -->
      </div>
    </div>

    <!-- RESULTADOS -->
    <br />
    <br>
    <div class="resultados">
      <h1 class="title is-3">RESULTADOS</h1>
      <div class="columns is-mobile">
        <!-- Aqui pintamos todos los resultados, OJO!! ense;amos el array gracias a la funcion "TodosLosResultados", si pusieramos aqui el array no hace na -->
        <div class="column" v-for="item in resultados" :key="item">
          <p v-if="item == 6 | item == 5" class="acierto">{{ item }} </p>
          <p v-if="item == 1 " class="fatal">{{ item }} </p>
          <p v-if="item != 1 && item != 5 && item != 6 ">{{ item }} </p>
        </div>
      </div>
      <div class="suma">
        <h1 class="title">Suma de todo</h1>
        <p class="subtitle">{{ SumaDetodo }}{{ this.sumaResultado }}</p>
      </div>
      <hr />
    </div>
  </div>
</template>

<script>
export default {
  name: "juego de Dados",
  data() {
    return {
      // Variables necesarias para ver CUANTOS DADOS y CANTAS CARAS necesitamos
      NDeLados: "6",
      NDeDados: "",
      resultados: [1, 6, 5, 3],
      sumaResultado: 0,
    };
  },
  methods: {
    async tirarDados(min, max) {
      max = this.NDeLados; // declaramos el maximo (loindicado arriba en el formualrio)
      await this.vaciarArray(); // vaciamos el array de resultados
      for (let i = 0; i < this.NDeDados; i++) {
        // un bucle normal
        this.resultado = Math.floor(Math.random() * (min, max)) + min;
        console.log(this.resultado);
        this.resultados.push(this.resultado); // en cada vuelta metemos el resultado ene l array
      }
    },

    vaciarArray: function () {
      this.resultados = []; // vaciamos el array de resultado
      this.sumaResultado = 0;
    },
  },
  computed: {
    SumaDetodo: function () {
      for (let i = 0; i < this.resultados.length; i++) {
        this.sumaResultado += this.resultados[i];
      }
    },
  },
};
</script>

<style scoped>

.acierto{
  background-color: rgb(0, 255, 0);
  border: 1mm ridge rgba(211, 220, 50, .6);
}
.fatal{
  background-color: rgb(255, 124, 124);
  border: 1mm ridge rgba(220, 50, 50, 0.6);
}
.BGJuegos{
  background-image: url("https://img.freepik.com/free-vector/white-gold-hexagon-pattern-background_53876-115292.jpg?w=2000");
  min-height: 100vh;
  background-position: center;
  background-size: cover;
  

}

</style>
