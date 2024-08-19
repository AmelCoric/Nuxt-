<template>
  <div>
    <h1>Besplatne igre</h1>
    <CategoryFilter :categories="categories" @filter="fetchGamesByCategory"/>
    <div class="games-list">
      <GameCard v-for="game in games" :key="game.id" :game="game"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import GameCard from '~/components/GameCard.vue';
import CategoryFilter from '~/components/CategoryFilter.vue';


export default {
  data() {
    return {
      games: [],
      categories: ['Shooter', 'Racing', 'Sports', 'MMORPG', 'Strategy'], 
    };
  },
  async fetch() {
    const { data } = await axios.get('https://www.freetogame.com/api/games');
    this.games = data.slice(0, 20); 
  },
  methods: {
    async fetchGamesByCategory(category) {
      const { data } = await axios.get(`https://www.freetogame.com/api/games?category=${category}`);
      this.games = data.slice(0, 20); 
    },
  },
  components: {
    GameCard,
    CategoryFilter,
  }
}
</script>

<style scoped>
.games-list {
  display: flex;
  flex-wrap: wrap;
 
}
</style>