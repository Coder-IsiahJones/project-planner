<template>
  <div class="home">
    <FilterNav
      @updateFilter="currentFilter = $event"
      :currentFilter="currentFilter"
    />
    <div v-if="projects.length">
      <div v-for="project in filteredProjects" :key="project.id">
        <SingleProject
          :project="project"
          @delete="handleDelete"
          @complete="handleComplete"
        />
      </div>
    </div>
  </div>
</template>

<script>
import SingleProject from "../components/SingleProject.vue";
import FilterNav from "../components/FilterNav.vue";

export default {
  name: "HomeView",
  components: { SingleProject, FilterNav },
  data() {
    return {
      projects: [],
      currentFilter: "all",
    };
  },
  mounted() {
    fetch("http://localhost:3000/projects")
      .then((response) => response.json())
      .then((data) => (this.projects = data))
      .catch((error) => console.log(error));
  },
  methods: {
    handleDelete(id) {
      this.projects = this.projects.filter((project) => {
        return project.id !== id;
      });
    },
    handleComplete(id) {
      let projectIndex = this.projects.find((project) => {
        return project.id === id;
      });
      projectIndex.complete = !projectIndex.complete;
    },
  },
  computed: {
    filteredProjects() {
      if (this.currentFilter === "completed") {
        return this.projects.filter((project) => project.complete);
      } else if (this.currentFilter === "ongoing") {
        return this.projects.filter((project) => !project.complete);
      }
      return this.projects;
    },
  },
};
</script>
