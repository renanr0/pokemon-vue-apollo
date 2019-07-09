<template>
  <div class="pokemon">
    <ApolloQuery
      :query="require('../graphql/pokemon.gql')"
      :variables="{ name }"
      class='container'
    >
      <template slot-scope="{ result: { loading, error, data }, isLoading }" >
        <div class='loading-container' v-if="isLoading">
          <Loading />
        </div>
        <div class='details-box' v-if='data && !isLoading'> 
          <div class='box-max-container' >
            <BoxMax class='box-max' :max='{title: "Max HP", value: data.pokemon.maxHP}' />
            <BoxMax class='box-max' :max='{title: "Max CP", value: data.pokemon.maxCP}' />
          </div>
          <div>
            <h3>Fast Attacks</h3>
            <AttackTable :attacks='data.pokemon.attacks.fast' />
            <h3>Special Attacks</h3>
            <AttackTable :attacks='data.pokemon.attacks.special' />
          </div>
        </div>
      </template>
    </ApolloQuery>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import gql from 'graphql-tag'
import TypeBadge from '@/components/TypeBadge.vue'
import BoxMax from '@/components/BoxMax.vue'
import AttackTable from '@/components/AttackTable.vue'
import Loading from '@/components/Loading.vue'

@Component({
  components: {
    TypeBadge,
    BoxMax,
    AttackTable,
    Loading
  }
})
export default class PokemonDetails extends Vue {
  private name = '';

  mounted() {
    setTimeout(() => {
      this.name = this.$route.params.name;
    }, 300);
  }
}

</script>

<style scoped lang="scss">
  .pokemon {
    width: 265px;
    height: 390px;
    background: radial-gradient(#F8F8F8, #E0E0E0);
    padding: 10px;
    border-radius: 5px;
    border: 1px solid #E1E1E1;
  }

  h3 {
    margin: 5px 0;
  }

  .details-box {
    width: 100%;
  }

  .loading-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .types {
    display: flex;
  }

  .box-max-container {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }

  .box-max {
    width: 47%;
  }

  .type-item {
    font-size: small;
    color:white;
    background: green;
    border-radius: 5px;
    padding: 5px;
  }

  .container{
    height: 100%;
  }

</style>
