<template>
  <div>
    <h1>{{ job.title }}</h1>
    <p>{{ job.slug }}</p>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  data() {
    return {
      job: {},
    }
  },
  async fetch() {
    const response = await this.$apollo.query({
      query: gql`
        query {
          job(
            input: {
              jobSlug: "senior-fullstack-engineer-platform"
              companySlug: "segment"
            }
          ) {
            title
            slug
            description
          }
        }
      `,
    })

    this.job = response.data.job
  },
}
</script>
