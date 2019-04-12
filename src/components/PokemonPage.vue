<template>
    <div id="pokemonPage">
        <div id="pokemonPageHeader">
            {{id}} - {{name}}

        </div>
        <div id="pokemonPageImages">
            <div class="pokemonSprite" v-for="(sprite, key) in sprites">
                {{key}}
                <img v-bind:src="sprite" />
            </div>
        </div>
        <div id="pokemonPageDetails">
            Height (m): {{heightMeters}}
            Weight (kg): {{weightKg}}
        </div>
    </div>
</template>

<script>
export default {
  name: 'PokemonPage',
  props: {
    id: Number
  },
  data() {
      return {
          name : '',
          weightKg: 0,
          heightMeters: 0,
          sprites: {}
      };
  },
  methods: {
      getData: async function() {
          let pokedata = await fetch('https://pokeapi.co/api/v2/pokemon/25/');
          let data = await pokedata.json();
          console.log(data);
          this.name = data.name;
          this.weightKg = data.weight / 10;
          this.heightMeters = data.height / 10;
          this.sprites = data.sprites;
          // Object.keys(data.sprites).forEach(key => {
          //     this.sprites.push(data.sprites[key]);
          // });
      },
      getSprites: async function(url) {
          console.log(url);
          return url;
      }
  },
  beforeMount() {
      this.getData();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
