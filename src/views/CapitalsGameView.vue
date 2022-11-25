<script>
import countries from "/src/datasets/countries.json";
import CountryComponent from "../components/CountryComponent.vue";

export default {
  name: "CapitalsGameView",
  components: {
    CountryComponent,
  },
  data() {
    return {
      countries: countries,
  },
  data() {
    return {
      country: {},
      capital: "",
      puntaje: 0,
    };
  },
  created() {
    this.country = countries[Math.floor(Math.random() * countries.length)];
  },
  methods: {
    setCapital(e) {
      //TODO: implementar. fija la capital del input.
      this.capital = e.target.value;
    },
    adivinarCapital() {
      //TODO: implementar. verifica se la adivinanza es correcta.


      if (this.capital.toLowerCase() === this.country.capital.toLowerCase()) {
        this.puntaje++;
        this.country = countries[Math.floor(Math.random() * countries.length)];
        this.capital = "";
      } else {
        alert("Incorrecto");
      }
    },
  },
};

</script>

<template>
  <h1>Puntaje: {{ puntaje }}</h1>
  <div class="countries">
    <!-- TODO: usar los metodos definidos arriba dentro del input para llenar el estado de la capital a adivinar-->
    <input
      placeholder="Adivina la capital"
      type="text"
      :value="this.capital"
      @input="setCapital"

    />  
    <button @click="adivinarCapital">Adivinar</button>

  </div>
  <div class="countries-container">
    

    <CountryComponent
      :name="country.name"
      :capital="country.capital"
      :currency_name="country.currency_name"
      :currency="country.currency"
      :region="country.region"
      :code="country.code"

    <input
      type="text"
      
      placeholder="Adivina la capital"
    />
    <button @click="adivinarCapital">Adivina!</button>
    <div class="countries-container">
      <!--TODO: CREAR EL COMPONENTE PARA VISUALIZAR EL PAIS-->

<template>
<div id="app">
<VuePolygonCropper :imageSource = "require('../assets/logo.png')"
ref="canvas"> </VuePolygonCropper>
<button @click.prevent="crop"> Crop </button>
<button @click.prevent="undo"> Undo </button>
<button @click.prevent="redo"> Redo </button>
<button @click.prevent="reset"> Reset </button>

</div>
</template>

<script>
import VuePolygonCropper from 'vue-polygon-cropper';
export
default
{
    name: 'App',
    components:{VuePolygonCropper},
    methods: {
        crop: function() {
            this.$refs.canvas.crop();
},
undo: function()
{
    this.$refs.canvas.undo();
},
redo: function()
{
    this.$refs.canvas.redo();
},
reset: function()
{
    this.$refs.canvas.reset();
}
}
};
</script>

    </div>
  </div>
</template>

<style scoped>
@media (min-width: 1024px) {
  .countries {
    align-items: center;
  }

  input {
    line-height: 2em;
  }

  .countries-container {
    margin-left: 35%;
    align-items: center;
    overflow-y: auto;
    vertical-align: middle;
    padding: 10px;
  }
}
</style>
