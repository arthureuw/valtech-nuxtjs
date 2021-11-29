<template>
  <v-chip-group
    active-class="primary--text"
  >
    <v-chip
      v-for="(letter, key) in alphabet"
      :key="key"
      @click="selectedLetter(letter)"
    >
      {{ letter.toUpperCase() }}
    </v-chip>
  </v-chip-group>
</template>
<script>
export default {
  props: {
    letters: Array
  },
  data() {
    return {
      alphabet: ["a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z"]
    }
  },
  methods: {
    selectedLetter(letter) {
      this.$emit('selectedLetter', letter)
    }
  }
}
</script>
