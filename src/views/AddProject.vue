<template>
  <form @submit.prevent="handleSubmit">
    <label>Title</label>
    <input type="text" v-model="title" required />
    <label>Details</label>
    <textarea v-model="details" required></textarea>
    <button>Add Project</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      details: "",
    };
  },
  methods: {
    handleSubmit() {
      let project = {
        title: this.title,
        details: this.details,
        complete: false,
      };
      console.log(project);

      fetch("http://localhost:3000/projects", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(project),
      })
        .then(() => {
          this.$router.push("/");
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style lang="scss">
form {
  background: white;
  padding: 1.3rem;
  border-radius: 0.625rem;

  label {
    display: block;
    color: #bbb;
    text-transform: uppercase;
    font-size: 0.875rem;
    font-weight: bold;
    letter-spacing: 0.0625rem;
    margin: 1.25rem 0 0.625rem 0;
  }

  input {
    padding: 0.625rem;
    border: 0;
    border-bottom: 0.0625rem solid #ddd;
    width: 100%;
    box-sizing: border-box;
  }

  textarea {
    border: 0.0625rem solid #ddd;
    padding: 0.625rem;
    width: 100%;
    box-sizing: border-box;
    height: 6.25rem;
  }

  button {
    display: block;
    margin: 1.25rem auto 0;
    background: #00ce89;
    color: white;
    padding: 0.625rem;
    border: 0;
    border-radius: 0.375rem;
    font-size: 1rem;
  }
}
</style>
