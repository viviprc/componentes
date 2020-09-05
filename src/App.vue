<template>
  <div>
    <div id="personajes" v-for="(character, i) in characters" :key="i">
      <Character :src="character.imagen" :characterName="character.nombre" />
    </div>
  </div>
</template>

<script>
import Character from "./components/Character";
export default {
  components: {
    Character,
  },

  data() {
    return {
      characters: [],
    };
  },
  mounted() {
    fetch("https://rickandmortyapi.com/api/character")
      .then((response) => response.json())
      .then((json) => {
        let info = json.results;
        info.slice(0, 5).forEach((e) => {
          let nombre = e.name;
          let imagen = e.image;
          this.characters.push({ nombre, imagen });
        });
      })
      .catch((err) => {
        console.log(`Algo anda mal {{err}}`);
      });
  },
};
</script>

<style>
body {
  background-image: url("https://images2.alphacoders.com/195/195750.jpg");
  background-size: cover;
  background-position: center;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  color: white;
}
#personajes {
  margin: 5px 80px;
}
.contenedor {
  display: flex;
  justify-content: left;
  align-items: center;
}
.imagen-personaje {
  width: 80px;
  border: 1px solid #281e5d;
  border-radius: 50%;
  margin: 10px;
}
</style>
