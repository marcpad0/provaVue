<template>
  <v-container>
    <v-card class="mx-auto" max-width="344" v-for="p in this.prodotti" :key="p.id">
      <v-img height="200px" :src="p.images[0]" cover></v-img>

      <v-card-title>
        {{ p.title }}
      </v-card-title>

      <v-card-subtitle>
        1,000 miles of wonder
      </v-card-subtitle>

      <v-card-actions>
        <v-btn color="orange-lighten-2" text="Explore"></v-btn>

        <v-spacer></v-spacer>

        <v-btn :icon="show ? 'mdi-chevron-up' : 'mdi-chevron-down'" @click="show = !show"></v-btn>
      </v-card-actions>

      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>

          <v-card-text>
            I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for
            sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you
            add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to
            escape.
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'HomeView',
  data() {
    return {
      prodotti: [],
      show: false,
    }
  },

  methods: {
    async getProdotti() {
      const response = await fetch('https://api.escuelajs.co/api/v1/products')
      const data = await response.json()
      this.prodotti = data
      console.log(this.prodotti)
    }
  },
  created() {
    this.getProdotti()
  },
  mounted() {

  }
}
</script>
