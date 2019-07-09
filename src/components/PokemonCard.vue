<template>
  <div class="pokemon">
    <div class='img-container'>
      <img :src="imageUrl" alt="">
    </div>
    <div class='bottom-container'>
      <div class='number-box'>
        <span class='number'>#{{ pokemon.number }}</span>
      </div>
      <div class='info-box'>
        <div class='infos'>
          <span class="pokemon-name"> {{ pokemon.name }} </span>
          <div class='types'>
            <TypeBadge 
              class='type'
              :type='type'
              v-for="type in pokemon.types"
              :key="type"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import TypeBadge from './TypeBadge.vue';
import pokemons from '@/assets/pokemons.json'

@Component({
  components: {
    TypeBadge
  }
})
export default class PokemonCard extends Vue {
  @Prop() private pokemon!: any

  data() {
    return {
      imageUrl: `https://assets.pokemon.com/assets/cms2/img/pokedex/full/${this.pokemon.number}.png`,
    }
  }
}
</script>

<style scoped lang="scss">
  .pokemon {
    width: 265px;
    height: 390px;
    background: radial-gradient(#f8f8f8, #E0E0E0);
    border-radius: 5px;
    border: 1px solid #E1E1E1;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    cursor: pointer;
  }

  .number-box {
    margin: 0 auto;
    background: white;
    width: min-content;
    padding: 10px;
    border-radius: 10px 10px 0px 0px;
    height: 35px;
    font-size: 20px;
    font-weight: bold;

    // &::before{
    //    content: '';
    //   position: absolute;
    //   height: calc(35px / 2);
    //   width: calc(35px / 2);
    //   background: white;
    //   z-index: 1;
    //   left: -18px;
    //   bottom: 0;
    // }
    
    // &::after {
    //   content: '';
    //   position: absolute;
    //   height: calc(35px / 2);
    //   width: calc(35px / 2);
    //   background: white;
    //   z-index: 1;
    //   bottom: 0;
    //   right: -18px;
    // }
  }

  //  attempt rounded tab; maybe came back
  // .number {
  //   position: relative;
  //   &::after {
  //     position: absolute;
  //     content: ' ';
  //     width: calc(35px / 2);
  //     height: calc(35px / 2);
  //     border-bottom-left-radius: 50%;
  //     background: #EBEBEB;
  //     z-index: 3;
  //     bottom: -1px;
  //     right: -29px;
  //   }
  // }
  .info-box {
    background: white;
    height: 85px;
    padding: 15px;
    border-radius: 0 0 5px 5px;

    .pokemon-name {
      font-weight: bold;
      font-size: 19px;
      line-height: 1.8em;
    }
  }

  .img-container {
    width: 100%;
    padding: 15px;
    img {
      max-width: 100%;
    }
  }

  .types {
    display: flex;
    .type {
      margin-right: 5px;
    }
  }

</style>
