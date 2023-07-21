<template>
  <button class="button" @click="onClick" :disabled="isDisabled">
    <span class="icon">
      <i :class="icone"></i>
    </span>
    <span>{{ texto }}</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "BotaoComponent",
  emits: ["onClick"],
  props: {
    isDisabled: {
      type: Boolean,
      default: false,
    },
    texto: {
      type: String,
      default: "Click me",
      required: true,
    },
    icone: {
      type: String,
      default: "fas fa-cursor",
      required: true,
    },
  },
  methods: {
    onClick(): void {
      this.$emit("onClick");
    },
  },
});
</script>
