<script setup lang="ts">
import { ref } from "vue";

const allClues = [
  { emoji:"🦵🦵🦵", text: "(3 legs)" },
  { emoji: "✈️✈️", text: "1h 20m from London Gatwick" },
  { emoji: "👑👑", text: "British Crown Dependency"},
  { emoji: "🚋🚋", text: "Steam trains!" },
  { emoji: "🏝️🏝️", text: "It's an island!" },
  { emoji: "❌❌", text: "It's not Ireland or Northern Ireland" },
  { emoji: "🇬🇧🇬🇧", text: "No visa or passport required" },
  { text: "Looks like this", img: "https://upload.wikimedia.org/wikipedia/commons/0/0f/Isle_of_Man_outline_map.png,"},
  { text: "Location: ", img: "https://ibb.co/YPQ1QXb"}
]

const count = ref(0);
const clues = ref<{ text: string; emoji?:string; img?: string }[]>([]);

const giveClue = () => {
  clues.value.push(allClues[count.value]);
  count.value++;
}
</script>

<template>
  <div style="display: grid; gap: 20px">
    <div v-for="clue in clues" :key="clue.text" style="display: grid; gap: 5px">
      <p style="font-family: Tahoma; font-size: 24px">{{ clue.emoji }}</p>
      <p style="font-family: Tahoma; font-size: 24px">{{ clue.text }}</p>
      <img v-if="clue.img" :src="clue.img" />

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
