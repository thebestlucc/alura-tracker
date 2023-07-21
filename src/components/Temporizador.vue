<template>
  <Cronometro :duracaoEmSegundos="duracaoEmSegundos" />
  <Botao
    @onClick="iniciar"
    :isDisabled="cronometroRodando"
    texto="start"
    icone="fas fa-play"
  />
  <Botao
    @onClick="finalizar"
    :isDisabled="!cronometroRodando"
    texto="stop"
    icone="fas fa-stop"
  />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from "./Cronometro.vue";
import Botao from "./Botao.vue";

export default defineComponent({
  name: "TemporizadorComponent",
  emits: ["aoTemporizadorFinalizado"],
  data() {
    return {
      duracaoEmSegundos: 0,
      intervalId: 0,
    };
  },
  computed: {
    cronometroRodando(): boolean {
      return this.intervalId !== 0;
    },
  },
  methods: {
    iniciar() {
      this.intervalId = setInterval(() => {
        this.duracaoEmSegundos += 1;
      }, 1000);
    },
    finalizar() {
      clearInterval(this.intervalId);
      this.intervalId = 0;
      this.$emit("aoTemporizadorFinalizado", this.duracaoEmSegundos);
      this.duracaoEmSegundos = 0;
    },
  },
  components: {
    Cronometro,
    Botao,
  },
});
</script>
