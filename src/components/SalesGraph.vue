<template>
  <v-card class="mx-auto" max-width="344">
    <v-img :src="sale.image" height="200px"></v-img>

    <v-card-title>
      {{ sale.title }}
    </v-card-title>

    <v-card-subtitle>
      {{ sale.sale }}
    </v-card-subtitle>
  </v-card>
</template>

<script>
export default {
  name: 'SalesGraph',
  props: ['sale'],
}
</script>

<style scoped></style>
