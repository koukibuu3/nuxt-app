<template>
  <container>
    <ul>
      <li v-for="content in contents" :key="content.id">
        <nuxt-link :to="`/blog/${content.id}`">
          {{ content.title }}
        </nuxt-link>
      </li>
    </ul>
  </container>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData () {
    const { data } = await axios.get(
      'https://koukibuu3.microcms.io/api/v1/blog',
      {
        headers: { 'X-API-KEY': 'bf85970e-5d65-41d0-b10a-a79db1d510ed' }
      }
    )
    return data
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
