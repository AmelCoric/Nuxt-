<template>
  <div>
    <label for="category">Filter by Category:</label>
    <select id="category" @change="onFilterChange">
      <option value="">All</option>
      <option v-for="category in categories" :key="category" :value="category">{{ category }}</option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    categories: Array,
  },
  methods: {
    onFilterChange(event) {
      this.$emit('filter', event.target.value);
    }
  }
}
</script>