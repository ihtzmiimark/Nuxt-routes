<template>
  <div class="container">
    <div class="">
      <logo />
      <div style="margin: 0 auto; display:flexbox; width: fit-content;">
        <div style="text-align: center;">
          <h2 class="Title" style="color:skyblue">River's View </h2>
          <NuxtLink to="/about">About</NuxtLink>
          <NuxtLink to="/">Home</NuxtLink>
        </div>
       <ul
          style="size: 30px; font-size:larger; margin: 0 auto; display:flex; width: 100%; list-style-type: none; margin-top: 30px; margin-bottom: 30px;">
          <li style="margin-left: 25px;" v-for="river in rivers" :key="river.slug">
            <NuxtLink :to="river.slug">
              {{ river.title }}
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
    this.rivers = await fetch('https://api.nuxtjs.dev/rivers').then(res => res.json())
  },
  data() {
    return {
      rivers: [],
    }
  },

}



</script>

<style lang="scss" scoped>

</style>