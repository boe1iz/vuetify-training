<template>
  <v-container>
    <h1>Dashboard</h1>
    <v-row>
      <v-col v-for="sale in sales" :key="`${sale.title}`">
        <SalesGraph :sale="sale" />
      </v-col>
    </v-row>
    <v-row>
      <v-col v-for="statistic in statistics" :key="`${statistic.title}`">
        <StatisticsCard :statistic="statistic" />
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="8">
        <v-data-table
          :headers="headers"
          :items="desserts"
          :items-per-page="5"
          class="elevation-1"
          @click:row="selectRow"
        ></v-data-table>
        <v-snackbar v-model="snackbar">
          {{ currentItem }}
          <v-btn color="pink" text @click="snackbar = false">
            Close
          </v-btn>
        </v-snackbar>
      </v-col>
      <v-col>
        <EventTimeLine />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'Dashboard',
  components: {
    SalesGraph: () => import('@/components/SalesGraph.vue'),
    StatisticsCard: () => import('@/components/StatisticsCard.vue'),
    EventTimeLine: () => import('@/components/EventTimeLine.vue'),
  },
  data() {
    return {
      snackbar: false,
      currentItem: '',
      headers: [
        {
          text: 'Dessert (100g serving)',
          align: 'start',
          sortable: false,
          value: 'name',
        },
        { text: 'Calories', value: 'calories' },
        { text: 'Fat (g)', value: 'fat' },
        { text: 'Carbs (g)', value: 'carbs' },
        { text: 'Protein (g)', value: 'protein' },
        { text: 'Iron (%)', value: 'iron' },
      ],
      desserts: [
        {
          name: 'Frozen Yogurt',
          calories: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
          iron: '1%',
        },
        {
          name: 'Ice cream sandwich',
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          iron: '1%',
        },
        {
          name: 'Eclair',
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          iron: '7%',
        },
        {
          name: 'Cupcake',
          calories: 305,
          fat: 3.7,
          carbs: 67,
          protein: 4.3,
          iron: '8%',
        },
        {
          name: 'Gingerbread',
          calories: 356,
          fat: 16.0,
          carbs: 49,
          protein: 3.9,
          iron: '16%',
        },
        {
          name: 'Jelly bean',
          calories: 375,
          fat: 0.0,
          carbs: 94,
          protein: 0.0,
          iron: '0%',
        },
        {
          name: 'Lollipop',
          calories: 392,
          fat: 0.2,
          carbs: 98,
          protein: 0,
          iron: '2%',
        },
        {
          name: 'Honeycomb',
          calories: 408,
          fat: 3.2,
          carbs: 87,
          protein: 6.5,
          iron: '45%',
        },
        {
          name: 'Donut',
          calories: 452,
          fat: 25.0,
          carbs: 51,
          protein: 4.9,
          iron: '22%',
        },
        {
          name: 'KitKat',
          calories: 518,
          fat: 26.0,
          carbs: 65,
          protein: 7,
          iron: '6%',
        },
      ],
      sales: [
        {
          title: 'Car',
          sale: '1.500',
          image: 'https://cdn.vuetifyjs.com/images/cards/cooking.png',
        },
        {
          title: 'Home',
          sale: '10.500',
          image: 'https://cdn.vuetifyjs.com/images/cards/sunshine.jpg',
        },
        {
          title: 'Computer',
          sale: '250',
          image: 'https://cdn.vuetifyjs.com/images/cards/mountain.jpg',
        },
      ],
      statistics: [
        {
          title: 'Employees',
          stat: '65',
        },
        {
          title: 'Ream Sold',
          stat: '983.000',
        },
        {
          title: 'Rating',
          stat: '4.5',
        },
        {
          title: 'Revenue',
          stat: '$2.3M',
        },
      ],
    }
  },
  methods: {
    selectRow(event) {
      this.snackbar = true
      this.currentItem = event.name
    },
  },
}
</script>

<style scoped></style>
