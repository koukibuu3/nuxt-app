<template>
  <main x-if="data" class="main">
    <h1 class="title">
      {{ data.title }}
    </h1>
    <p class="publishedAt">
      {{ data.publishedAt }}
    </p>
    <div class="post">
      {{ data.introduction }}
    </div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      data: { title: 'hoge' }
    }
  },
  async created () {
    const query = this.$route.query
    if (query.id === undefined || query.draftKey === undefined) {
      return
    }
    const { data } = await axios.get(
      `https://koukibuu3.microcms.io/api/v1/blog/${query.id}?draftKey=${query.draftKey}`,
      {
        headers: { 'X-API-KEY': 'bf85970e-5d65-41d0-b10a-a79db1d510ed' }
      }
    )
    this.data = data
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
