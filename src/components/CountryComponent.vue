<script>
export default {
  name: "CountryComponent",
  props: [
    "name",
    "capital",
    "currency_name",
    "currency",
    "region",
    "code",
    //TODO: crear una propiedad para determinar si al componente se le puede hacer click
    "clickable",
  ],
};
</script>

<template>
  <!--TODO: Utilizar la propiedad creada para controlar el click. Cuando el componente es "clickeable", redirigir a la pagina del pais.
  Mira las rutas para ver como redirigir al usuario.-->
  <div class="country">
    <div class="country__flag">
      <img :src="'https://www.countryflags.io/' + code + '/flat/64.png'" />
    </div>
    <div class="country__info">
      <h2>{{ name }}</h2>
      <p>{{ capital }}</p>
      <p>{{ currency_name }} ({{ currency }})</p>
      <p>{{ region }}</p>
    </div>
    
  <div
  >
  <!--TODO: Poblar el HTML con las propiedades. Usar https://countryflagsapi.com/png/${code}-->

</template>

<div v-if="getError">
  <div v-for="(_errors, key) in getError">
    <b-alert
      v-for="error in _errors"
      show
      variant="danger"
    >
      <h2>{{ formatKey(key) }} :</h2>
      <li>{{ error }}</li>
    </b-alert>
  </div>
</div>

export default {
  methods: {
    formatKey (key) {
      return this.$t('vue.' + key.replace('contract_data.', ''))
    }
  }
}

<style scoped>
.country {
  padding: 2px;
  white-space: nowrap;
  width: 350px;
  height: 350px;
  border-style: solid;
  border-radius: 5px;
  border-color: grey;
}

.country-hover:hover {
  background-color: rgb(49, 49, 49);
  cursor: pointer;
}

h1 {
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>

.city { 
  padding: 2px; 
  white-space: nowrap; 
  width: 350px; 
  height: 350px; 
  border-style: solid; 
  border-radius: 5px; 
  border-color: grey; 
} 
 
h1 { 
  overflow: hidden; 
  text-overflow: ellipsis; 
} 