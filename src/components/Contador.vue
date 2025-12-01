<template>
  <div>
    <h1>{{ tit }}</h1>
    <!--Para usar js en el template se usan {{}}-->
    <p>
      {{ numero }} <sup>{{ exp }}</sup> = {{ calculaCuadrado }}
    </p>
    <p>{{ numero }} <sup>2</sup> = {{ calculaCuadrado }}</p>
    <p>{{ numero }} <sup>2</sup> = {{ calculaCuadrado }}</p>
    <p>{{ numero }} <sup>2</sup> = {{ calculaCuadrado }}</p>
    <p>{{ numero }} <sup>3</sup> = {{ obtenerCubo() }}</p>
    <div>
      <!--Las directivas en vue son plabras clave que permite a vue manipular el DOM de manera reactiva
      toda directica en vue empieza con (v-)-->
      <button v-on:click="incrementar()">+1</button>
      <!--El v-on tiene un shortcut también el cual es (@)-->
      <button @:click="decrementar()">-1</button>
      <!--v-if y v-show no tienen diferencia visual pero el v-if construye o no construye el elemento
      mientras que el v-show solo tiene un estilo para q no se vea -->
      <button v-show="mostrar">prueba</button>
      <button v-if="mostrar">prueba</button>
    </div>
  </div>
</template>

<script>
export default {
  //Estructura por defecto para declarar option API: dentro del script se declaran secciones
  // Propiedades reactivas son variables a usar dentro de mi componente
  // Se llaman reactivas porq al hacer un cambio en la sección de js, reactivamente actualiza la página
  // Así se declaran:
  data() {
    return {
      numero: this.inicio,
      exp: 0,
      titulo: "Contador",
      joffre_manco: true,
    };
  },
  // Primero se declaran las propiedades reactivas luego los methods
  methods: {
    obtenerCuadrado() {
      console.log("Entró a obtener cuadrado");
      return this.numero * this.numero;
    },
    obtenerCubo() {
      return this.numero * this.numero * this.numero;
    },
    incrementar() {
      console.log(this.tit);
      this.numero++;
      this.exp++;
    },
    decrementar() {
      this.numero--;
      this.exp--;
    },
  },
  // Propiedades computadas: se declaran como metodos pero no son metodos, se ejecutan solo cuando
  // ocurre un resultado cambia el resultado de la ejecución de su cuerpo y siempre se guardan en cache
  computed: {
    calculaCuadrado() {
      console.log("Entra a propiedad computada");
      return this.numero * this.numero;
    },
    calculaCubo() {
      return this.numero * this.numero * this.numero;
    },
  },
  // Los props son variables a nivel de componente que yo puedo instanciar o puedo darles un valor desde un componente externo a componente
  // y son llenadas desde el padre
  // Es la forma de comunicarse entre un componente padre y un componente hijo
  /* props: ["tit", "inicio", "mostrar"], declaración básica de props*/
  props: {
    tit: String,
    inicio: {
      type: Number,
      default: 99,
      validator(value) {
        return value > 10;
      },
    },
    mostrar: Boolean,
  },
};
/* Todos los tipos: String, Number, Boolean, Array, Object, Date, Funciones, BigInt*/
</script>

<style>
button {
  border: 1px solid black;
  background-color: aqua;
}
</style>