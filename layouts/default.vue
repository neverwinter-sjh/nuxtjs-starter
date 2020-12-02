<template>
  <div>
    <Logo />
    <div>
      <nav>
        <ul>
          <li>
            <NuxtLink to="/">Home</NuxtLink>
          </li>
          <li>
            <NuxtLink to="/about">About Page</NuxtLink>
          </li>
        </ul>
      </nav>
    </div>
    <Nuxt />
  </div>
</template>
<script>
import Logo from '~/components/Logo';

export default {
  components: {
    Logo
  },
  // before ssr rendering
  asyncData() {
    return {};
  },
  mounted() {
    console.log('layout mounted');
  }
};
</script>

<style></style>
