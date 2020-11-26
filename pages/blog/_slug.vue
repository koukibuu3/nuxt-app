<template>
  <main class="main">
    <h1 class="title">
      {{ title }}
    </h1>
    <p class="publishedAt">
      {{ publishedAt }}
    </p>
    <div class="post">
      {{ introduction }}
    </div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData ({ params }) {
    const { data } = await axios.get(
      `https://koukibuu3.microcms.io/api/v1/blog/${params.slug}`,
      {
        headers: { 'X-API-KEY': 'bf85970e-5d65-41d0-b10a-a79db1d510ed' }
      }
    )
    return data
  }
}
</script>

<style lang="scss" scoped>
.main {
  width: 960px;
  margin: 0 auto;
}

.title {
  display: block;
  font-weight: 300;
  font-size: 50px;
  color: #35495e;
  letter-spacing: 1px;
}

.publishedAt {
  margin-bottom: 40px;
}
</style>
