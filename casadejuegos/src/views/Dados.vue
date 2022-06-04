<template>
<div>
  <a href="/"><Hero/></a>
  

  <JuegoDados/>
</div>
  
</template>

<script>
import Hero from '@/components/Hero.vue'
import JuegoDados from '@/components/JuegoDados.vue'


export default {
  name: 'Dados',
  components: {
    Hero,
    JuegoDados
  }

}
</script>

<style>

</style>