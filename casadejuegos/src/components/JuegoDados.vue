<template>
  <div class="app">
    <div class="container">
      <br />

      <!-- FORMULARIO -->
      <div class="formulario columns">
        <div class="column">
          <p>Numero de DADOS</p>
          <input type="number" v-model="NDeDados" />
        </div>
        <div class="column">
          <p>Numero de LADOS</p>
          <input type="number" v-model="NDeLados" />
        </div>
      </div>

      <!-- BOTOND DE LANZAR DADOS -->
      <!-- Aqui indicamos ya el minimo del resultado que debe salir y el maximo lo indicamos con "NDeLados" -->
      <button @click="tirarDados(1)" class="button is-warning is-active">
        TIRAR!
      </button>
    </div>

      <!-- RESULTADOS -->
    <br />
    <div class="resultados">
      <h1 class="title is-3">RESULTADOS</h1>
      <ul class="columns">

        <!-- Aqui pintamos todos los resultados, OJO!! ense;amos el array gracias a la funcion "TodosLosResultados", si pusieramos aqui el array no hace na -->
        <li v-for="item in TodosLosResultados" :key="item" class="column">
          {{item}}
        </li>
        
      </ul>
      <hr />
      <!-- <p class="title is-1">{{ resultado }}</p> -->
    </div>

  </div>
</template>

<script>
export default {
  name: "juego de Dados",
  data() {
    return {
      // Variables necesarias para ver CUANTOS DADOS y CANTAS CARAS necesitamos
      NDeLados: '',
      NDeDados: '',
      // resultado: "XXXX",
      // Array para guardar los resultados y despues mostrarlos
      resultados:[
        "Ejemplo", 13
      ],
    };
  },
  methods: {
    tirarDados: function (min, max) {
      max = this.NDeLados // declaramos el maximo (loindicado arriba en el formualrio)
      this.resultados = [] // vaciamos el array de resultados
      for (let i = 0; i < this.NDeDados; i++) {
        // un bucle normal
        this.resultado = Math.floor(Math.random() * (min, max))+ min;
        console.log(this.resultado);
        this.resultados.push(this.resultado)// en cada vuelta metemos el resultado ene l array
      }
      //  return this.resultado
    },
  },
  computed: {
      TodosLosResultados: function () {// hacemos una funcion para enseñar todos los resultados dentro del array
       //si no hacemos esta funcion, el array ava  estar ahi pero no va a enseñar nada
        return this.resultados
      },
    
  }
};
</script>

<style>
/* .app {
  color: red;
} */
</style>