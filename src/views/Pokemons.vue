<template>
  <div class='home'>
    <ApolloQuery
      :query="require('../graphql/pokemons.gql')"
      :variables="{ first }"
      class='container'
    >
      <template slot-scope="{ result: { loading, error, data } }" v-if="data">
        <div v-for="pokemon in data.pokemons" :key="pokemon.id">
          <router-link :to="pokemon.name" >
            <div v-on:click='openDetail(pokemon.name)' v-if='pokemon.name !== getNamePokemonDetails()'>
              <PokemonCard 
                :pokemon="pokemon"
                class="pokemon-card"
                />
            </div>
          </router-link>
          <router-view  v-if='pokemon.name == getNamePokemonDetails()'></router-view>
        </div>
      </template>
    </ApolloQuery>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';
import PokemonCard from '@/components/PokemonCard.vue'; 
import PokemonDetails from '@/components/PokemonDetails.vue';
import gql from 'graphql-tag'

@Component({
  components: {
    PokemonCard,
    PokemonDetails
  },
})
export default class Pokemons extends Vue {
  public namePokemonDetails = '';

  data() {
    return {
      first: 30,
      namePokemonDetails: this.$route.params.name
    }
  }

  openDetail(name: string):void {
    this.namePokemonDetails = name;
  }
  
  getNamePokemonDetails():string {
    return this.namePokemonDetails;
  }
}
</script>
<style lang="scss">
  .home {
    max-width: 80%;
    margin: 0 auto;
  }

  .container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  .pokemon-card {
    margin: 10px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  } 

  @media (max-width:767px) {
    .home {
        max-width: 100%;
      }
  }
</style>

