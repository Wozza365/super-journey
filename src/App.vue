<script setup lang="ts">
import { ref } from "vue";

const allClues = [
  { text: "🦵🦵🦵 (3 legs)" }
]

const count = ref(0);
const clues = ref<{ text: string }[]>([]);

const giveClue = () => {
  clues.value.push(allClues[count.value]);
  count.value++;
}
</script>

<template>
  <div>
    <div v-for="clue in clues" :key="clue">
      {{  clue.text }}
    </div>

    <button @click="giveClue">Give me a clue!</button>

    <input type="text" placeholder="Take a guess!!!" />
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
