<template>
  <main class="main-content">
    <SearchForm />
    <div class="container">
      <div class="card-wrapper">
        <div v-for="country in countries" :key="country.cca2">
          <router-link :to="{
            name: 'detail',
            params: {
              alphaCode: country.cca2
            }
          }"><Card :country="country"/>
          </router-link>
        </div>
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
  },
  data() {
    return {
      KEY: `https://restcountries.com/v3.1/all`,
      countries: []
    }
  },
  methods: {
    async getData() {
      const request = await fetch(this.KEY)
      return request.json()
    }
  },
  mounted() {
    this.getData().then((data) => {
      this.countries = data
    })
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