<template>
  <div class='box'>
    <div class='title'>
      {{max.title}}
    </div>
    <div class='value'>
      {{max.value}}
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component export default class BoxMax extends Vue {
  @Prop() private max!: any
}
</script>

<style scoped lang="scss">
  .title {
    text-transform: uppercase;
    font-size: small;
    color: #A3A3A3;
    font-weight: 700;
  }

  .value {
    text-align: center;
    font-weight: bolder;
    line-height: 1.7em;
  }

  .box {
    padding: 2px;
    background: #EEEEEE;
    height: 45px;
    border: 1px solid #E1E1E1;
  }
</style>
