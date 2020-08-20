<template>
  <div class="container">
    <div v-for="country in countries" :key="country.name" class="country-box">
      <div class="img-container">
        <router-link :to="{path: country.name.toLowerCase(), params: country.name }">
          <img :src="country.flag" alt />
        </router-link>
      </div>
      <p>{{country.name}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "CountryList",

  data() {
    return {
      countries: [],
    };
  },

  created() {
    this.$axios.get("https://restcountries.eu/rest/v2/all").then((response) => {
      this.countries = response.data;
      console.log(this.response);
    });
  },

  methods: {
    trim(str) {
      //remove whitespace from url link and convert strings to lower case
      str = str.toLowerCase();
      return str.replace(/\s/g, "");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  /* max-width: 1124px; */
  margin: auto;
  background-color: whitesmoke;
}

@media (min-width: 640px) {
  .container > * {
    width: 40%;
  }
}

@media (min-width: 768px) {
  .container > * {
    width: 25%;
  }
}

@media (min-width: 1024px) {
  .container > * {
    width: 15%;
  }
  img {
    height: 100px;
  }
}

.country-box {
  margin: 20px;
}

.img-container {
  background-color: antiquewhite;
}

img {
  width: 100%;
  object-fit: cover;
  filter: drop-shadow(0px 3px 3px rgba(0, 0, 0, 0.4));
}

a:hover img {
  filter: drop-shadow(0px 3px 3px rgba(0, 0, 0, 1));
}

p {
  text-align: center;
}
</style>


