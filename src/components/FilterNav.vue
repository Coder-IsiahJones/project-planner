<template>
  <nav class="filter-nav">
    <button
      :class="{ active: currentFilter === 'all' }"
      @click="updateFilter('all')"
    >
      View All
    </button>
    <button
      :class="{ active: currentFilter === 'completed' }"
      @click="updateFilter('completed')"
    >
      Completed
    </button>
    <button
      :class="{ active: currentFilter === 'ongoing' }"
      @click="updateFilter('ongoing')"
    >
      Ongoing
    </button>
  </nav>
</template>

<script>
export default {
  props: ["currentFilter"],
  methods: {
    updateFilter(filter) {
      this.$emit("updateFilter", filter);
    },
  },
};
</script>

<style lang="scss" scoped>
.filter-nav {
  button {
    background: none;
    border: none;
    color: #bbb;
    outline: none;
    font-size: 0.75rem;
    text-transform: uppercase;
    margin-right: 0.625rem;
    letter-spacing: 0.0625rem;
    font-weight: bold;
    cursor: pointer;
  }

  .active {
    color: #555;
  }
}
</style>
