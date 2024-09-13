<script>
import {Laureate} from "../model/laureate.entity.js";

export default {
  name: "laureate-item",
  props:{
    laureate: {type: Laureate, required: true}
  }
};
</script>

<template>
  <pv-card style="margin: 20px" aria-label="Laureate card">
    <template #title>{{$t('card.full_name')}}: {{laureate.firstname}} {{laureate.surname}}</template>
    <template #subtitle>ID: {{laureate.id}}</template>
    <template #content>
      <p>{{$t('card.born')}}: {{laureate.born}}</p>
      <p>{{$t('card.gender')}}: {{laureate.gender}}</p>
      <p>{{$t('card.number_prizes')}}: {{laureate.prizes.length}}</p>
    </template>
  </pv-card>
</template>

<style scoped>

</style>