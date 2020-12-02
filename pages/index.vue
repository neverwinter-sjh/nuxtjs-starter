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
import Mountains from '~/components/common/Mountains.vue';

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

<style></style>
