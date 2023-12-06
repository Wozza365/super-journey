<script setup lang="ts">
import { ref } from "vue";

const allClues = [
  { emoji:"🦵🦵🦵", text: "(3 legs)" },
  { emoji: "✈️✈️", text: "1h 20m from London Gatwick" },
  { emoji: "👑👑", text: "British Crown Dependency"},
  { emoji: "🚋🚋", text: "Steam trains and old trams!" },
  { emoji: "🏝️🏝️", text: "It's an island!" },
  { emoji: "❌❌", text: "It's not Ireland or Northern Ireland" },
  { emoji: "🇬🇧🇬🇧", text: "No visa or passport required" },
  { text: "Looks like this", img: "https://upload.wikimedia.org/wikipedia/commons/0/0f/Isle_of_Man_outline_map.png"},
  { text: "Location: ", img: "https://i.ibb.co/RYbsbN7/IoM.png"},
  { text: "No more clues :("}
]

const count = ref(0);
const clues = ref<{ text: string; emoji?:string; img?: string }[]>([]);

const answer = ref("");

const giveClue = () => {
  clues.value.push(allClues[count.value]);
  count.value++;
  setTimeout(() => {
    window.scrollTo(0, document.body.scrollHeight + 50);
  }, 1000)
}
</script>

<template>
  <div v-if="answer.toLowerCase() !== 'isle of man'" style="display: grid; gap: 20px">
    <p v-if="count === 0" style="font-size: 36px">Gotta guess your gift :P</p>
    <transition-group name="list">
      <div v-for="clue in clues" :key="clue.text" style="display: grid; gap: 5px">
        <p style="font-size: 36px">{{ clue.emoji }}</p>
        <p >{{ clue.text }}</p>
        <img v-if="clue.img" :src="clue.img" style="width: 100%" />
      </div>
    </transition-group>


    <button @click="giveClue" style="padding: 16px; font-size: 24px;" :disabled="clues.length === allClues.length">Give me a clue!</button>

    <input type="text" v-model="answer" placeholder="Take a guess!!!" style="
      padding: 16px;
      font-size: 24px;
    " />
  </div>
  <div v-else style="display: grid; gap: 20px">
    <img src="https://cdn.britannica.com/52/1752-050-06659B9E/Flag-Isle-of-Man.jpg" width="100%" />
    <p>✈️ London Gatwick -> Douglas 08:00 21/03/2024</p>
    <p>✈️ Douglas -> London Gatwick 20:00 24/03/2024</p>
    <p>Sea view hotel ⛵⛵</p>
    <img src="https://cf.bstatic.com/xdata/images/hotel/max1024x768/36845289.jpg?k=3ba11e74cf48a9b38aeca54bea0528d9ba311a27c315575036464303bd4576a5&o=" width="100%" />
    <p>Some of the scenery:</p>
    <img src="https://ichef.bbci.co.uk/news/976/cpsprodpb/FF50/production/_102606356_mediaitem102606355.jpg" width="100%" />
    <img src="https://a.cdn-hotels.com/gdcs/production148/d743/0e2ef5ac-c2b9-47c1-9e4c-3bacea6ed58b.jpg" width="100%" />
    <img src="https://www.celtictrailswalkingholidays.co.uk/wp-content/uploads/2012/02/Peel-Castle.jpg" width="100%" />
  </div>
</template>

<style scoped>
p {
  font-size: 24px;
  font-family: Tahoma;
}

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

.list-move, /* apply transition to moving elements */
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}

/* ensure leaving items are taken out of layout flow so that moving
   animations can be calculated correctly. */
.list-leave-active {
  position: absolute;
}
</style>
