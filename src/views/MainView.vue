<template>
  <main class="main-content">
    <SearchForm />
    <div class="container">
      <div class="card-wrapper">
        <Card />
      </div>
    </div>
  </main>
</template>

<script>
import SearchForm from '@/components/SearchForm.vue'
import Card from '@/components/Card.vue'

export default {
  name: "MainView",
  components: {
    SearchForm,
    Card
  }
}
</script>

<style scoped>
.main-content {
  background-color: var(--main-bg);
}

.card-wrapper {
  display: flex;
  flex-wrap: wrap;
  gap: 74px;
}
</style>