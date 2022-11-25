<script>
import countries from "/src/datasets/countries.json";
import CountryComponent from "../components/CountryComponent.vue";

export default {
  name: "CountriesView",
  components: {
    CountryComponent,
  },
  data() {
    return {
      countries: [],
      paisActual: "",
    };
  },
  created() {
    this.countries = countries;
  },
  methods: {
    filtrarPais(e) {
      // TODO: Implementar. filtra el país de acuerdo al valor del input. Hint: Recuerda la función filter
      this.paisActual = e.target.value;
      this.countries = countries.filter((country) => {
        return country.name.toLowerCase().includes(this.paisActual.toLowerCase());
      });
      const filtro = e.target.value;
    },
  },
};
</script>

<template>
  <div class="countries">
    <input
      placeholder="Busca un país"
      type="text"
      :value="this.paisActual"
      @input = "filtrarPais"
    />
  </div>
  <div class="countries-container">
    <!--//TODO: pasar una propiedad para determinar si al componente se le puede hacer click -->
    <CountryComponent
      v-for="(country, index) in countries"
      :key="index"
      :name="country.name"
      :capital="country.capital"
      :region="country.region"
      :subregion="country.subregion"
      :population="country.population"
      :flag="country.flag"
      :languages="country.languages"
      :borders="country.borders"
      :clickable="true"
    />
</template>

<style scoped>
@media (min-width: 1024px) {
  .countries {
    display: flex;
    align-items: center;
  }

  input {
    line-height: 2em;
  }

  .countries-container {
    text-align: center;
    overflow-y: auto;
    vertical-align: middle;
    display: grid;
    grid-template-columns: auto auto auto;
    grid-gap: 10px;
    padding: 10px;
  }
}
</style>
