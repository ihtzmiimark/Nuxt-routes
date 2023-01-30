<template>
  <div class="container">
    <div>
      <img :src="river.image" alt="" />
      <h1 class="title">{{ river.title }}</h1>
      <h1>{{ river.description }}</h1>
      <h1>{{ river.length }}</h1>
      <RiversList />
    </div>
  </div>
</template>

<script>
export default {
  transition: 'bounce',
  head() {
    return {
      title: this.river.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.river.description,
        },
      ],
      link: [
        {
          hid: 'canonical',
          rel: 'canonical',
          href: `https://jamstack-explorers-nuxt-mission`,
        },
      ],
    }
  },
  async asyncData({ params }) {
    const river = await fetch(
      `https://api.nuxtjs.dev/rivers/${params.slug}`
    ).then((res) => {
      if (res.ok) {
        return res.json()
      }
      throw new Error(res.status)
    })
    return { river }

  },
  mounted() {
    console.log(this.river)
  }
}
</script>
<style scoped>
h1 {
  font-family: Nunito, sans-serif;
}

img {
  height: 80px;
  width: auto;
  object-fit: cover;
}
</style>
