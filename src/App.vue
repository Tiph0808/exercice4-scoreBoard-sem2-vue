<script setup>
import { reactive } from 'vue'

const users = reactive([
  {
    id: 1,
    alias: 'Alfred',
    gender: 'male',
    age: 32,
    level: 'Expert',
    numberOfWin: 2,
    actualScore: 0,
  },
  {
    id: 2,
    alias: 'Lisa',
    gender: 'female',
    age: 29,
    level: 'Intermediate',
    numberOfWin: 1,
    actualScore: 0,
  },
])

const addOnePoint = (player) => {
  if (player === 'Alfred') {
    users[0].actualScore = users[0].actualScore + 1
  } else if (player === 'Lisa') {
    users[1].actualScore = users[1].actualScore + 1
  }
}

const addTwoPoints = (player) => {
  if (player === 'Alfred') {
    users[0].actualScore = users[0].actualScore + 2
  } else if (player === 'Lisa') {
    users[1].actualScore = users[1].actualScore + 2
  }
}

const addFivePoints = (player) => {
  if (player === 'Alfred') {
    users[0].actualScore = users[0].actualScore + 5
  } else if (player === 'Lisa') {
    users[1].actualScore = users[1].actualScore + 5
  }
}

const resetCounters = () => {
  users[0].actualScore = 0
  users[1].actualScore = 0
}

const addPoints = (player, points) => {
  if (player === 'Alfred') {
    users[0].actualScore = users[0].actualScore + points
  } else if (player === 'Lisa') {
    users[1].actualScore = users[1].actualScore + points
  }
}

const pointsValueList = reactive([1, 2, 5])
</script>

<template>
  <div v-for="user in users" :key="user.id">
    <div class="player">
      <p>{{ user.alias }}</p>
      <p>{{ user.age }}</p>
      <p>{{ user.level }}</p>
    </div>

    <p>
      {{ user.gender === 'female' ? 'she' : 'he' }} has already {{ user.numberOfWin }}
      {{ user.numberOfWin > 1 ? 'victories' : 'victory' }}
    </p>

    <div>
      <p>Actual Score</p>
      <p>{{ user.actualScore }}</p>
    </div>

    <!-- <div>
      <button @click="addOnePoint(user.alias)">Add 1 point</button>
      <button @click="addTwoPoints(user.alias)">Add 2 points</button>
      <button @click="addFivePoints(user.alias)">Add 5 points</button>
    </div> -->

    <!-- <div>
      <button @click="addPoints(user.alias, 1)">Add 1 point</button>
      <button @click="addPoints(user.alias, 2)">Add 2 point</button>
      <button @click="addPoints(user.alias, 5)">Add 5 point</button>
    </div> -->

    <div>
      <button
        v-for="(number, index) in pointsValueList"
        :key="index"
        @click="addPoints(user.alias, number)"
      >
        Add {{ number }} {{ number > 1 ? 'points' : 'point' }}
      </button>
    </div>
  </div>

  <button @click="resetCounters">Reset</button>
</template>

<style scoped></style>
