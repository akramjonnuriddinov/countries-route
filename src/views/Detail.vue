<template>
  <div class="detail">
    <div class="container detail__container">
      <button class="back-btn" @click="$router.go(-1)">
        <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
          <g id="call-made">
            <path id="Shape" fill-rule="evenodd" clip-rule="evenodd" d="M6.46447 4.10744L7.64298 5.28596L3.75389 9.17504L18.6031 9.17504L18.6031 10.825L3.75389 10.825L7.64298 14.714L6.46447 15.8926L0.57191 10L6.46447 4.10744Z" fill="currentColor"/>
          </g>
        </svg>
        <span>Back</span>
      </button>
      <div class="detail__content">
        <img class="detail__img" :src="img_url" width="560" height="401" alt="">
        <div class="detail__info">
          <h3 class="detail__title">{{ alphaCode }}</h3>
          <div class="more-info">
            <div>
              <p class="detail__text">
                <span class="detail__text--bold">Native Name: </span>
                <span class="detail__text--small">{{ name }}</span>
              </p>
              <p class="detail__text">
                <span class="detail__text--bold">Population: </span>
                <span class="detail__text--small">{{ country.population }}</span>
              </p>
              <p class="detail__text">
                <span class="detail__text--bold">Region: </span>
                <span class="detail__text--small">{{ country.region }}</span>
              </p>
              <p class="detail__text">
                <span class="detail__text--bold">Sub Region: </span>
                <span class="detail__text--small">{{ country.subregion }}</span>
              </p>
              <p class="detail__text">
                <span class="detail__text--bold">Capital: </span>
                <span class="detail__text--small">{{ capital }}</span>
              </p>
            </div>
            <div>
              <p class="detail__text">
                <span class="detail__text--bold">Top Level Domain: </span>
                <span class="detail__text--small">{{ domain }}</span>
              </p>
              <p class="detail__text">
                <span class="detail__text--bold">Currencies: </span>
                <span class="detail__text--small">{{ currencies }}</span>
              </p>
              <p class="detail__text">
                <span class="detail__text--bold">Languages: </span>
                <span class="detail__text--small">{{ languages }}</span>
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['alphaCode'],
  data() {
    return {
      country: [],
      KEY: `https://restcountries.com/v3.1/alpha/`,
      name: '',
      capital: '',
      img_url: '',
      languages: '',
      currencies: '',
      domain: ''
    }
  },
  mounted() {
    this.getData().then((data) => {
      this.country = data[0]
      console.log(data[0])
      this.capital = this.country.capital[0]
      this.name = this.country.name.common
      this.img_url = this.country.flags.png
      this.languages = this.country.languages
      this.currencies = this.country.currencies
      this.domain = this.country.tld[0]
    })
  },
  methods: {
    async getData() {
      const request = await fetch(this.KEY + this.alphaCode)
      return request.json()
    }
  },
}
</script>

<style scoped>
.detail {
  padding-top: 80px;
  background-color: var(--main-bg);
  padding-bottom: 80px;
  width: 100%;
  height: 100%;
}

.detail__content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.detail__img {
  border-radius: 10px;
}

.detail__info {
  max-width: 598px;
  width: 100%;
}

.more-info {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}

.detail__title {
  margin-top: 0;
  margin-bottom: 23px;
  font-weight: 800;
  font-size: 32px;
  line-height: 43.65px;
  color: var(--text-color);
}

.detail__text {
  margin-top: 0;
  margin-bottom: 0;
  font-size: 16px;
  line-height: 32px;
  font-weight: 400;
}

.detail__text--bold {
  font-weight: 800;
}

.back-btn {
  background-color: var(--white);
  color: var(--text-color);
  border: none;
  display: flex;
  align-items: center;
  gap: 10px;
  font-weight: 300;
  font-size: 16px;
  box-shadow: 0px 0px 7px 0px var(--shadow-color);
  border-radius: 6px;
  line-height: 20px;
  padding: 10px 39px 10px 32px;
  cursor: pointer;
  margin-bottom: 80px;
}
</style>