<template>
  <div>
    <div>
      <div v-for="country in countries" :key="country.name">
        <div class="detail-container">
          <div class="img-container">
            <img :src="country.flag" alt />
          </div>

          <div>
            <p>Country Name: {{country.name}}</p>
            <p v-if="country.capital">Capital: {{country.capital}}</p>
            <p>Region: {{country.region}}</p>
            <p v-if="country.subregion">Sub Region: {{country.subregion}}</p>
            <p>Population: {{country.population}}</p>
            <p>Native Name: {{country.nativeName}}</p>
            <p>Top Level Domain: {{country.topLevelDomain[0]}}</p>
            <p>Alpha2 Code: {{ country.alpha2Code }}</p>
            <p>Alpha3 Code: {{ country.alpha3Code }}</p>

            <p>Calling Code: {{country.callingCodes[0]}}</p>
            <p>Alt Spelling: {{country.altSpellings[0]}}</p>

            <p>Numeric Code: {{country.numericCode}}</p>
            <p>Area Number: {{country.area}}</p>
            <p>Time Zone: {{country.timezones[0]}}</p>

            <p v-if="country.cioc">Cioc: {{country.cioc}}</p>

            <p>
              Geo:
              <span>Lat:{{ country.latlng[0] }}, Long:{{country.latlng[1]}}</span>
            </p>

            <p>Demonym: {{country.demonym}}</p>
            <p v-if="country.area">Area: {{country.area}}</p>
            <p v-if="country.gini">Gini: {{country.gini}}</p>
            <p v-if="country.borders.length > 0">Borders: {{country.borders[0]}}</p>

            <div>
              Languages:
              <ul>
                <li v-for="(language, index) in country.languages" :key="index">{{ language.name }}</li>
              </ul>
            </div>
            <div>
              Translations:
              <ul>
                <li
                  v-for="(translation, index) in country.translations"
                  :key="index"
                >{{ index }}: {{ translation }}</li>
              </ul>
            </div>

            <div>
              Currencies:
              <ul>
                <li
                  v-for="(currency, index) in country.currencies"
                  :key="index"
                >{{ currency.code }}: {{ currency.name }}</li>
              </ul>
            </div>

            <div v-if="country.regionalBlocs.length > 0">
              Regional Bloc:
              <ul>
                <li
                  v-for="(regional, index) in country.regionalBlocs"
                  :key="index"
                >{{ regional.acronym }} - {{ regional.name }}</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SingleCountry",
  props: ["name"],

  data() {
    return {
      countries: [],
    };
  },

  created() {
    this.$axios
      .get(`https://restcountries.eu/rest/v2/name/${this.name}?fullText=true`)
      .then((response) => (this.countries = response.data));
  },
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.detail-container {
  padding: 0 5%;
  padding-bottom: 2%;
}

@media (min-width: 768px) {
  .detail-container {
    display: flex;
  }

  .img-container {
    margin-right: 6%;
  }

  img {
    min-height: 200px;
  }
}

@media (min-width: 1024px) {
  img {
    height: 300px;
  }
}

.img-container {
  max-width: 350px;
  max-height: 300px;
}

img {
  width: 100%;
  max-height: 100%;
  filter: drop-shadow(0px 3px 3px rgba(0, 0, 0, 0.4));
  object-fit: cover;
}
</style>


