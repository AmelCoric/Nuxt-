<template>
  <div>
    <h1>{{ game?.title }}</h1>
    <img :src="game?.thumbnail" alt="Game image">
    <p>{{ game?.short_description }}</p>
    <a :href="game?.game_url" target="_blank">Igraj</a>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  async asyncData({ params }) {
    const { data } = await axios.get(`https://www.freetogame.com/api/game?id=${params.id}`);
    return { game: data };
  },
}
</script>