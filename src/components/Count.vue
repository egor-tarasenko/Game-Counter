<template>
  <div class="d-inline-block me-3">{{ character.title }}</div>
  <div class="btn-group btn-group-sm" role="group" aria-label="Basic example">
    <button type="button" class="btn btn-outline-primary" @click="decrement">-</button>
    <button type="button" class="btn btn-primary" readonly>{{ count }}</button>
    <button type="button" class="btn btn-outline-primary" @click="increment">+</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
    };
  },
  props: {
    character: {
      required: true,
      type: Object,
    },
    totalPoints: {
      required: true,
      type: Number,
    },
  },
  methods: {
    decrement() {
      if (this.count > 0) {
        this.count--;
        this.updateCharacter()
      }
    },
    increment() {
      if (this.totalPoints > 0) {
        this.count++
        this.updateCharacter()
      }
    },
    updateCharacter() {
      let updateCharacter = { ...this.character }
      updateCharacter.count = this.count
      this.$emit('changeCharacter', updateCharacter)
    },
  },
}
</script>


