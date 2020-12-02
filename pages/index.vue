<template>
  <div>
    <h1>Home Page</h1>
    <h2>Data fetched using asyncData</h2>
    <ul>
      <li v-for="mountain in mountains" :key="mountain.title">
        <NuxtLink :to="{ name: 'mountains-slug', params: { slug: mountain.slug } }">
          {{ mountain.title }}
        </NuxtLink>
      </li>
    </ul>
    <hr />
    <hr />
    <Mountains />
  </div>
</template>

<script>
import Mountains from '~/components/Mountains.vue';
export default {
  components: { Mountains },
  // before ssr rendering
  async asyncData({ $axios }) {
    const mountains = await $axios.$get('https://api.nuxtjs.dev/mountains');
    return { mountains };
  },
  mounted() {
    console.log('index mounted');
    console.log(this.$axios);
  }
};
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

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue',
    Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
