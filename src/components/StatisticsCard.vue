<template>
  <div>
    <v-card>
      <v-card-title>{{ statistic.title }}</v-card-title>
      <v-card-subtitle>{{ statistic.stat }}</v-card-subtitle>
    </v-card>
  </div>
</template>

<script>
export default {
  name: 'StatisticsCard',
  props: ['statistic'],
}
</script>

<style scoped></style>
