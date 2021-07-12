<template>
  <div class="mx-auto my-10 content-container">
    <div v-for="job in jobs" :key="job.id" class="mb-10">
      <h1 class="text-4xl font-bold">{{ job.title }}</h1>
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  data() {
    return {
      jobs: [],
    }
  },

  async fetch() {
    const response = await this.$apollo.query({
      query: gql`
        query {
          jobs {
            id
            title
            slug
            cities {
              name
              slug
            }
          }
        }
      `,
    })

    this.jobs = response.data.jobs
  },
}
</script>
