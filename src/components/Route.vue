<template>
  <div class="route" v-for="border_country in border_countries">
    <p class="route__text">{{ border_country }}</p>
  </div>
</template>

<script>
export default {
  name: 'Route',
  props: ['border_countries']
}
</script>

<style scoped>
.route {
  box-shadow: 0px 0px 4px 1px var(--shadow-color);
  padding: 4px 28px;
  border: 1px solid var(--border-color);
  border-radius: 2px;
}

.route__text {
  color: var(--text-color);
  font-size: 13px;
  line-height: 19.1px;
  font-weight: 300;
  margin: 0;
}
</style>