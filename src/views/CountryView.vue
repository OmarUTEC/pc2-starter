<script>
import countries from "/src/datasets/countries.json";

export default {
  name: "CountryView",
  components: {},
  data() {
    return {
      country: {},
    };
  },
  created() {
    this.country = countries.find(
      (country) => country.iso2 === this.$route.params.code
    );
  },
  methods: {},
};
</script>

<template>
  <div class="country">
    <!--TODO: Poblar el HTML con las propiedades. Usar https://countryflagsapi.com para la bandera-->
    <h1>{{ country.name }}</h1>
   <template v-slot:selection="slotProps">
     <i :class="['mr-2', 'em', slotProps.item.flag]"></i>
       <span>{{ slotProps.item.name }}</span>
   </template>
    <h2>{{ country.capital }}</h2>

    <img :src="country.flag" alt="bandera" />
    <p>{{ country.currency_name }} ({{ country.currency }})</p>

    <h1>{{ country.name }}</h1>
    <img :src="country.flag" />
    <p>Capital: {{ country.capital }}</p>
    <p>Moneda: {{ country.currency_name }} ({{ country.currency }})</p>
    <img
      width="400"
      height="400"
    />
    <div class="traducciones">
      <h2>Traducciones</h2>
      <h3
        v-for="(translation, index) in Object.keys(country.translations)"
        :key="index"
      >
        {{ `${translation}: ${country.translations[translation]}` }}
      </h3>
    </div>
  </div>
</template>

<style scoped>
.country {
  font-size: large;
}

@media (min-width: 1024px) {
}

.traducciones {
  color: white;
  display: grid;
}

.nombre {
  font-size: 50px;
}
</style>