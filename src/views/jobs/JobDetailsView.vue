<!-- @format -->

<template>
  <div v-if="job">
    <h1>Job Details Pge</h1>
    <h2>{{ job.title }}</h2>
    <p>{{ job.details }}</p>
    <p>The job id is {{ id }}</p>
  </div>

  <div v-else>Loading.....</div>
</template>

<script>
export default {
  data() {
    return {
      job: null,
    };
  },
  props: ["id"],
  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.job = data))
      .catch((err) => console.log(err.message));
  },

  //   data() {
  //     return {
  //       id: this.$route.params.id,
  //     };
  //   },
};
</script>

<style scoped></style>
