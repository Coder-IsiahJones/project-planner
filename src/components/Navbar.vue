<template>
  <nav class="main-nav">
    <router-link to="/">Projects</router-link>
    <router-link to="/add">Add Project</router-link>
  </nav>
</template>

<script>
export default {};
</script>

<style lang="scss">
.main-nav {
  text-align: center;
  margin: 2.5rem auto;

  a {
    display: inline-block;
    text-decoration: none;
    margin: 0 0.625rem;
    color: #999;
    font-size: 1.125rem;
  }

  a.router-link-active {
    border-bottom: 0.125rem solid #00ce89;
    padding-bottom: 0.25rem;
  }
}
</style>
