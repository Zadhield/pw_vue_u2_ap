<template>
  <PokemonImagen :pokemonId="pokemonGanador" />
  <PokemonOpciones
    @seleccionado="evaluarGanador($event)"
    :listaPokemons="pokemonArr"
  />
  <p v-if="mensaje">{{ mensaje }}</p>
</template>

<script>
import {
  obteneAleatorioFachada,
  obtenerVectorPokemonFachada,
} from "@/clients/PokemonClient";
import PokemonImagen from "@/components/PokemonImagen.vue";
import PokemonOpciones from "@/components/PokemonOpciones.vue";
export default {
  components: {
    PokemonImagen,
    PokemonOpciones,
  },
  data() {
    return {
      pokemonArr: [],
      pokemonGanador: null,
      mensaje: null,
    };
  },
  mounted() {
    console.log("componente¡ montado");
    this.iniciarJuego();
  },
  methods: {
    async iniciarJuego() {
      this.pokemonArr = await obtenerVectorPokemonFachada();
      const idAleatorio = obteneAleatorioFachada(0, 3);
      this.pokemonGanador = this.pokemonArr[idAleatorio].id;
    },
    evaluarGanador(idGanador) {
      console.log("valor recibido desde el padre");
      console.log(idGanador);
      if (idGanador === this.pokemonGanador) {
        this.mensaje = "ganaste";
      } else {
        this.mensaje = "perdiste";
      }
    },
  },
};
</script>

<style>
p {
  text-align: center;
  font-weight: bold;
  color: blue;
}
</style>