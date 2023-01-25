<template>
  <div class="container">
    <div>
      <logo />
      <div style="margin: 0 auto; display:block; width: fit-content;">
      <div style="text-align: center;">
        <h1 class="Title">HOME</h1>
      <NuxtLink to="/about">About</NuxtLink>
      <NuxtLink to="/">Home</NuxtLink>
      </div>
      <ul style="margin: 0 auto; display:flex; width: 100%; list-style-type: none; margin-top: 10px;">
        <li style="margin-left: 30px;" v-for="planet in planets" :key="planet.slug">
          <NuxtLink :to="planet.slug">
            {{ planet.title }}
          </NuxtLink>
        </li>
      </ul>
    </div>
  </div>
  </div>

</template>

<script>
export default {
  async fetch() {
    this.planets = await fetch('https://api.nuxtjs.dev/planets').then (res => res.json())
  },
  data() {
    return {
      planets: [],
    }
  },
  
}



</script>

<style lang="scss" scoped>

</style>