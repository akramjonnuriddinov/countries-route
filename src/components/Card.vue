<template>
  <div class="card">
    <img class="card__img" :src="country.flags.png" width="267" height="160" alt="">
    <div class="card__content">
      <h1 class="card__title">{{ country.name.common }}</h1>
      <p class="card__text">
        <span class="card__text--bold">Population: </span>
        <span class="card__text--small">{{ country.population }}</span>
      </p>
      <p class="card__text">
        <span class="card__text--bold">Region: </span>
        <span class="card__text--small">{{ country.region }}</span>
      </p>
      <p class="card__text">
        <span class="card__text--bold">Capital: </span>
        <span class="card__text--small">{{ capital }}</span>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    country: {
      type: Object
    }
  },
  data() {
    return {
      capital: this.country.capital
    }
  }
}
</script>

<style>
.card {
  max-width: 264px;
  border-radius: 5px;
  width: 100%;
  padding-bottom: 46px;
  background-color: var(--white);
  box-shadow: 0px 0px 7px 2px var(--shadow-color);
}

.card__img {
  width: 100%;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
  object-fit: cover;
}

.card__content {
  padding: 24px 24px 0 24px;
  color: var(--text-color);
}

.card__title {
  margin-top: 0;
  margin-bottom: 16px;
  font-weight: 800;
  font-size: 18px;
  line-height: 26px;
  color: var(--text-color);
}
a:-webkit-any-link {
  text-decoration: none;
}

.card__text {
  font-size: 14px;
  line-height: 16px;
  margin-top: 0;
  font-weight: 300;
}

.card__text:not(:last-child) {
  margin-bottom: 8px;
}

.card__text--bold {
  font-weight: 600;
}
</style>