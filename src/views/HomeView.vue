<template>
  <div class="container">
    <h1>Memory</h1>

    <div class="card__numbers">
      <p>Bitte die Anzahl der Karten auswählen</p>
      <select name="NumberOfCards" id="NumberOfCards" v-model.number="NumberOfCards">
        <option disabled value="">Auswahl</option>
        <option>8</option>
        <option>16</option>
        <option>32</option>
        <option>256</option>
      </select>
    </div>
    <div class="playground">
      <div class="pair" v-for="(card, index) in NumberOfCards" :key="card">
        <div class="front" @click="showMsg(index)" :class="{ hidden: isHidden === index }"></div>
        <div class="back"></div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  data() {
    let NumberOfCards = ref()

    return {
      NumberOfCards,
      isActive: false,
      isHidden: null
    }
  },
  methods: {
    showMsg(i) {
      this.isHidden = i
    }
  }
}
</script>

<style scoped>
.card__numbers {
  display: flex;
  gap: 2rem;
}

.playground {
  width: 100%;
  display: flex;
  gap: 2rem;
  flex-wrap: wrap;
}

.pair {
  position: relative;
  border: 1px solid rgb(52, 52, 52);
  width: 150px;
  height: 150px;
}

.front {
  cursor: pointer;
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: blue;
}

.back {
  cursor: pointer;
  width: 100%;
  height: 100%;
  background: lightblue;
}

.hidden {
  display: none;
}
</style>
