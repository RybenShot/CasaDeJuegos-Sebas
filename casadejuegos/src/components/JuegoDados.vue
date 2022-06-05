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
          <p>Numero de LADOS </p>
          <input type="number" v-model="NDeLados" />
        </div>
      </div>
 

      <!-- BOTOND DE LANZAR DADOS -->
      <!-- Aqui indicamos ya el minimo del resultado que debe salir y el maximo lo indicamos con "NDeLados" -->
      <div class="columns is-mobile">
      <button @click="tirarDados(1)" class="column button is-warning is-active mx-5">TIRAR!</button>
      <button @click="vaciarArray()" class="column button is-danger is-active mx-5">Vaciar</button>
      </div>
    </div>

      <!-- RESULTADOS -->
    <br />
    <div class="resultados">
      <h1 class="title is-3">RESULTADOS</h1>
      <div class="columns is-mobile">

        <!-- Aqui pintamos todos los resultados, OJO!! ense;amos el array gracias a la funcion "TodosLosResultados", si pusieramos aqui el array no hace na -->
        <div class="column " v-for="item in resultados" :key="item" >
          {{item}}
        </div>
      </div>
      <div class="suma">
        <h1 class="title"> Suma de todo</h1>
        <p class="subtitle">{{SumaDetodo}}{{this.sumaResultado}}</p>
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
      NDeLados: '6',
      NDeDados: '',
      resultados:[
        3, 13
      ],
      sumaResultado: 0
    };
  },
  methods: {
    async tirarDados(min, max) {
      max = this.NDeLados // declaramos el maximo (loindicado arriba en el formualrio)
      await this.vaciarArray() // vaciamos el array de resultados
      for (let i = 0; i < this.NDeDados; i++) {
        // un bucle normal
        this.resultado = Math.floor(Math.random() * (min, max))+ min;
        console.log(this.resultado);
        this.resultados.push(this.resultado)// en cada vuelta metemos el resultado ene l array
      }
    },

    vaciarArray: function () {
      this.resultados = [] // vaciamos el array de resultado
      this.sumaResultado = 0
    }
  },
  computed: {
      SumaDetodo: function(){
        for (let i = 0; i < this.resultados.length; i++) {
          this.sumaResultado += this.resultados[i]
          
        }
      }
    
  }
};
</script>

<style>
/* .app {
  color: red;
} */
</style>