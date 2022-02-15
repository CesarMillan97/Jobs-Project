<template>
<div v-if="job">
   <h1>Job Details Page</h1>
   <h1>Job title: {{ job.title }} </h1>
   <p>The job id is {{ job.id }} </p>
   <p>The job details is {{ job.details }} </p>
</div>
<div v-else>
   <h3>Loading details...</h3>
</div>
</template>

<script>
export default {
   props: ['id', 'details'],
   data(){
      return {
         job: null
      }
   },
   mounted(){
      fetch('http://localhost:3000/jobs/' + this.id)
      .then((res) => res.json())
      .then(data => this.job = data)
      .catch(err => console.log(err.message));
   }
}
</script>

<style>

</style>