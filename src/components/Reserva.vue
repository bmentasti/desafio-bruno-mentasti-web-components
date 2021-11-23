<template>
  <div id="app">
    <v-app id="reserva">
      <v-card
          :loading="loading"
          class="mx-auto my-12"
          max-width="550"
      >
        <template slot="progress">
          <v-progress-linear
              color="blue"
              height="10"
              indeterminate
          ></v-progress-linear>
        </template>
        <v-carousel class="images">
          <v-carousel-item
              v-for="(item,i) in images"
              :key="i"
              :src="item.src"
          ></v-carousel-item>
        </v-carousel>
        <v-card-title>{{ restoName }}</v-card-title>
        <v-card-text>
          <v-row
              align="center"
              class="mx-0"
          >
            <v-rating
                :value=restoStars
                color="amber"
                dense
                half-increments
                readonly
                size="14"
            ></v-rating>
            <div class="grey--text ms-4">
              {{ restoStars }} ({{restoOpinions}})
            </div>
          </v-row>
          <div class="my-4 text-subtitle-1">
            {{ restoType }}
          </div>
          <div>{{ restoDescription }}</div>
        </v-card-text>
        <v-divider class="mx-4"></v-divider>
        <v-card-title>{{ restoReserveNight }}</v-card-title>
        <v-card-text>
          <v-chip-group
              v-model="selection"
              active-class="blue accent-4 white--text"
              column
          >
            <v-chip v-for="item in restoReserveHours" :key="item.hours" @click="time(item)">{{ item.hours }}</v-chip>
          </v-chip-group>
        </v-card-text>
        <v-divider class="mx-4"></v-divider>
        <v-card-actions>
          <v-btn
              color="blue"
              text
              @click="reserve"
          >
            {{ restoReserveTitle }}
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-app>
  </div>
</template>

<script>
  export default {
    name: 'Reserva',

    data: () => ({
      loading: false,
      selection: 1,
      restoName: "Pizzeria El Fortin",
      restoStars: 4.5,
      restoOpinions: 517,
      restoType:"Pizzeria, Cafe",
      restoDescription:"El Fortín es una famosa pizzería del barrio de Monte Castro en su límite con Villa Luro, con una clientela tan consecuente que podría ser comparada con una hinchada. Bullicio, amigos, gente que entra y sale; buena iluminación y rapidez, hacen de El Fortín un lugar acogedor al que vale la pena ir, pero sin dudas la calidez y la atención de su gente, te hacen sentir ganas de volver.",
      restoReserveNight:"Horarios de Reserva",
      restoReserveHours: [
        { hours: '19:30hs' },
        { hours: '20:00hs' },
        { hours: '20:30hs' },
        { hours: '21:00hs' },
        { hours: '21:30hs' },
        { hours: '22:00hs' },
      ],
      restoReserveTitle:"Reservar",
      images: [
        { src: 'https://images.pagina12.com.ar/styles/width960/public/media/articles/54630/el-20fort-c3-adn.jpg?itok=g9swdvlQ' },
        { src: 'https://www.buenosaires.gob.ar/sites/gcaba/files/styles/interna_noticia/public/field/image/com10_fortin_web1.jpg?itok=HYnNYR4i'},
        { src: 'https://i.pinimg.com/originals/f3/aa/17/f3aa1721967b616936dd9425c1aafea1.jpg'}
      ],
    }),
    methods: {
      reserve() {
        this.loading = true
        setTimeout(() => (this.loading = false), 2000)
        console.log("La reserva fue confirmada")
      },
      time(item) {
        console.log(item.hours)
      },
    },
  }
</script>
<style>
.images{
  max-height: 300px;
}
</style>
