<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col">
        <h2>Characteristics: ({{ totalPoints }}/20)</h2>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <ul class="list-group list-group-flush">
          <li class="list-group-item" v-for="character in characteristics" :key="character.id">
            <Counter :character="character" :totalPoints="totalPoints" @changeCharacter="updateCharacteristics" />
          </li>
        </ul>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <pre>{{ characteristics }}</pre>
      </div>
    </div>
  </div>
</template>

<script>
import Counter from "./components/Count.vue"

export default {
  data() {
    return {
      totalPoints: 20,
      characteristics: [
        {
          id: 1,
          title: 'Health',
          count: 0,
        },
        {
          id: 2,
          title: 'Strength',
          count: 0,
        },
        {
          id: 3,
          title: 'Intelligence',
          count: 0,
        },
        {
          id: 4,
          title: 'Endurance',
          count: 0,
        },
        {
          id: 5,
          title: 'Mana',
          count: 0,
        },
        {
          id: 6,
          title: 'Armor',
          count: 0,
        },
        {
          id: 7,
          title: 'Speed',
          count: 0,
        },
      ],
    }
  },
  components: { Counter },
  methods: {
    updateCharacteristics(character) {
      let index = this.characteristics.findIndex((item) => item.id === character.id)
      if (index !== -1) {
        const countDifference = character.count - this.characteristics[index].count
        if (this.totalPoints >= countDifference) {
          this.totalPoints -= countDifference
          this.characteristics[index] = character
        } else {
          character.count = this.characteristics[index].count
        }
      }
    },
  },
}
</script>
