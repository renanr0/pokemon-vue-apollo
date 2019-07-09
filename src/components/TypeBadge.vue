<template>
  <span class="badge" :style="{ 'background': `${background}` }">
    {{ type }}
  </span>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import pokemons from '@/assets/pokemons.json';

enum TYPE_COLORS {
  Grass = '#75C236',  
  Poison = '#944896',
  Fire = '#ED3F0F',
  Flying = '#90A3F1',
  Water = '#3395F5',
  Bug ='#89960D',
  Normal = '#C5C0B6',
  Electric = '#E3AB27',
  Ground = '#D1B059',
  Fairy = '#F4B3F4',
  Fighting = '#80321B',
  Psychic = '#E55789',
  Rock = '#B59F57',
  Steel = '#B2B2BF',
  Ice = '#7DDAF8',
  Dragon = '#6464AD',
}

@Component export default class TypeBadge extends Vue {
  @Prop() private type!: string;

  get background () {
    // @ts-ignore
    return TYPE_COLORS[this.type];
  }
}
</script>

<style scoped lang="scss">
  .badge {
    font-size: small;
    color:white;
    border-radius: 5px;
    padding: 4px 5px;
    width: min-content;
  }
</style>
