<template>
 <div>
   <div class="text-center py-1-">
     <h1 class="text-4xl font-bold mb-2">Find the best jobs in the world</h1>
     <p class="text-gray-600 font-medium">We're the best job board in the entire world.</p>

   </div>
   <div class="mt-10">
     <job v-for="job in jobs" :key="job.id" :job="job"  />
   </div>

 </div>

</template>

<script>
  import gql from 'graphql-tag';
  import Job from "../components/Job";

  export default {
    components: {Job},
    apollo: {
      jobs: {
        query: gql`
          {
          jobs (
            orderBy: [{column: CREATED_AT, order: DESC}]
          ) {
            id,
            job_title,
            job_location,
            job_link,
            company_name,
            company_logo,
            hightlighted,
            tags {
              title,
              slug
            }
          }
          }
        `,
        fetchPolicy: 'network-only'
      }
    }
  }
</script>

