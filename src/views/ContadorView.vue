<template>
  <div>
     <!--V-bind todo lo que está dentro lo transforma a js, su shortcut es (:) los 2 puntos únicamente,
    se usa también para boleanos no solo para cadenas-->
    <Contador tit="Contador 1" v-bind:inicio="20" :mostrar="true" />
    <Contador tit="Contador 2" :inicio="4" :mostrar="false" />
  </div>
</template>

<script>
import Contador from '../components/Contador.vue'

export default {
    components:{
    Contador
    },

}
</script>

<style>

</style>