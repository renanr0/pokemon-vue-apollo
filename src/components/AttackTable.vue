<template>
  <table class='attacks'>
    <tr>
      <th class='start'> Attack </th>
      <th> Type </th>
      <th> Power </th>
    </tr>
    <tr v-for="(attack, i) in attacks" :key='i'>
      <td>{{ attack.name }}</td>
      <td class='center'><TypeBadge :type='attack.type' /></td>
      <td class='center'>{{ attack.damage }}</td>
    </tr>
  </table>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import TypeBadge from '@/components/TypeBadge.vue';

@Component({
  components: {
    TypeBadge
  }
}) export default class AttackTable extends Vue {
  @Prop() private attacks!: any
}
</script>

<style scoped lang="scss">
  .center {
    text-align: center;
  }
  .start {
    text-align: start;
  }
  table {
    width: 100%;
    font-size: small;
    td {
      line-height: 1.6em;
    }
  }
</style>
