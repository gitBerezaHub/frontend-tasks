<script setup>
import { ref } from 'vue'

const starQuantity = 5
const stars = ref(new Array(starQuantity).fill(false))
const total = ref(0)

function all (clickedStar) {
  stars.value.fill(false)
  for (let i = 0; i < clickedStar; i++) {
    stars.value[i] = true
  }
  total.value = clickedStar
}

</script>

<template>
  <div class="star-row">
    <div v-for="i in starQuantity"
         @click="all(i)" class="star">
      <img v-if="stars[i-1]" src="@/assets/star_filled.svg"
           width="75">
      <img v-else src="@/assets/star_blank.svg" width="75">
    </div>
  </div>
  <div class="total">
    <h1>Ваша оценка: {{ total}}</h1>
  </div>
</template>

<style scoped>
.star-row {
  width: fit-content;
  display: flex;
  flex-direction: row;
  border: 2px solid #000;
  border-radius: 16px;
}

.star {
  margin-right: 15px;
}
</style>