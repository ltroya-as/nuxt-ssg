<template>
  <div class="mx-auto my-10 content-container">
    <div v-for="user in users" :key="user.id" class="mb-10">
      <h1 class="text-4xl font-bold">{{ user.name.first }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: [],
    }
  },

  async fetch() {
    const response = await this.$axios.get(
      'https://randomuser.me/api?results=20'
    )
    this.users = response.data.results
  },
}
</script>
