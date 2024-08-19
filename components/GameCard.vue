<template>
  <div class="game-card">
    <img :src="game.thumbnail" alt="Game Image" />
    <h3>{{ game.title }}</h3>
    <p>{{ game.short_description }}</p>
    <nuxt-link :to="`/game/${game.id}`">Pogledaj Detalje</nuxt-link>
  </div>
</template>

<script>
export default {
  props: {
    game: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.game-card {
  width: 200px;
  margin: 10px;
  border: 1px solid #ccc;
  padding: 10px;
}
</style>