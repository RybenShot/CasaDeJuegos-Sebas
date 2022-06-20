<template>
  <div>
    <!-- <div class="columns is-mobile mt-3 mx-3">
      <button class="column button mx-2">
        <router-link to="/dados">Dados</router-link>
      </button>
      <button class="column button mx-2">
        <router-link to="/ruleta">Ruleta</router-link>
      </button>
    </div>

    <br />
    <div class="columns is-mobile mx-3">
      <button class="column button mx-2">
        <router-link to="/enproceso">Maquina expendedora</router-link>
      </button>
      <button class="column button mx-2">
        <router-link to="/enproceso">Cajero</router-link>
      </button>
    </div>
    <br />
    <div class="columns is-mobile mx-3">
      <button class="column button mx-2">
        <router-link to="/enproceso">Tragaperras</router-link>
      </button>
      <button class="column button mx-2">
        <router-link to="/enproceso">Piedra papel o tijeras</router-link>
      </button>
    </div> -->
    <div class="todo">
    <div class="container">
      <div @click="cambio(1)" class="panel " :class=" {active: img1}" style="background-image: url('https://www.xtrafondos.com/wallpapers/paisaje-digital-en-atardecer-5846.jpg')">
        <h3>Nombre random</h3>
      </div >
      <div @click="cambio(2)" class="panel" :class=" {active: img2}" style="background-image: url('https://fondosmil.com/fondo/2255.jpg')">
        <h3>Nombre random</h3>
      </div>
      <div @click="cambio(3)" class="panel" :class=" {active: img3}" style="background-image: url('https://fondosmil.com/fondo/11160.jpg')">
        <h3>Nombre random</h3>
      </div>
      <div @click="cambio(4)" class="panel" :class=" {active: img4}" style="background-image: url('https://www.proandroid.com/wp-content/uploads/2017/04/E36.jpg')">
        <h3>Nombre random</h3>
      </div>
      <div @click="cambio(5)" class="panel" :class=" {active: img5}" style="background-image: url('https://img.freepik.com/foto-gratis/hermoso-camino-madera-que-impresionantes-arboles-coloridos-bosque_181624-5840.jpg?w=2000')">
        <h3>Nombre random</h3>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  
  data(){
    return{
    img1: true,
    img2: false,
    img3: false,
    img4: false,
    img5: false
    }
    
  },
methods: {
  cambio : function(i){
    this.deleteAll()
    if (i == 1) {
      this.img1 = true
    }
    if (i == 2) {
      this.img2 = true
    }
    if (i == 3) {
      this.img3 = true
    }
    if (i == 4) {
      this.img4 = true
    }
    if (i == 5) {
      this.img5 = true
    }
  },
  deleteAll : function(){
    this.img1 = false;
    this.img2 = false;
    this.img3 = false;
    this.img4 = false;
    this.img5 = false
  }
}


};
</script>

<style scoped>

  @import url("https://fonts.googleapis.com/css2?family=Muli&display=swap");

*{
  box-sizing: border-box;
}

.todo{
  font-family: "Muli", sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  overflow: hidden;
  margin: 0;
  background: #ccc;
}
.container{
  display: flex;
  width: 90%;
}

.panel{
  background-size: auto 110%;
  background-position: center;
  background-repeat: no-repeat;
  height: 80vh;
  border-radius: 50px;
  color: #fff;
  cursor: pointer;
  flex: 0.5;
  margin: 10px;
  position: relative;
  transition: flex 0.7s ease-in;
  -webkit-transition: all 700ms ease-in;
}
.panel h3{
  font-size: 24px;
  position: absolute;
  bottom: 20px;
  left: 20px;
  margin: 0;
  opacity: 0;
}
.panel.active{
  flex: 5;
}
.panel.active h3{
  opacity: 1;
  transition: opacity 0.3s ease-in 0.4s;
}
@media(max-width: 480px){
  .container{
    width: 100%;
  }
  .panel:nth-of-type(4),
  .panel:nth-of-type(5){
    display: none;
  }
}

</style>