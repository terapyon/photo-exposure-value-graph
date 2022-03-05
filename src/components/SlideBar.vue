<template>
  <v-container>

  <v-card class="e4">
    <!-- <v-responsive
      :style="{ background: `rgb(${red}, ${green}, ${blue})` }"
      height="300px"
    ></v-responsive> -->

    <v-card-text>
      <v-container fluid>
        <v-row>
          <v-col cols="12">
            <v-slider
              v-model="ev"
              label="EV"
              :min="0"
              :max="evLabels.length -1"
              step="1"
              :tick-labels="evLabels"
              class="align-center"
            >
              <template v-slot:append>
                <v-text-field
                  v-model="ev"
                  class="mt-0 pt-0"
                  type="number"
                  style="width: 60px"
                ></v-text-field>
              </template>
            </v-slider>
          </v-col>

          <v-col cols="12">
            <v-slider
              v-model="tv"
              label="TV"
              :min="0"
              :max="tvLabels.length - 1"
              step="1"
              :tick-labels="tvLabels"
              class="align-center"
            >
              <template v-slot:append>
                <v-text-field
                  v-model="tv"
                  class="mt-0 pt-0"
                  type="number"
                  style="width: 60px"
                ></v-text-field>
              </template>
            </v-slider>
          </v-col>

          <v-col cols="12">
            <v-slider
              :value="calcAv"
              @input="av"
              label="AV"
              :min="0"
              :max="avLabels.length - 1"
              step="1"
              :tick-labels="avLabels"
              class="align-center"
              :readonly="true"
            >
              <template v-slot:append>
                <v-text-field
                  v-model="av"
                  class="mt-0 pt-0"
                  type="number"
                  style="width: 60px"
                ></v-text-field>
              </template>
            </v-slider>
          </v-col>

                    <v-col cols="12">
            <v-slider
              v-model="iso"
              label="ISO"
              :min="0"
              :max="isoLabels.length - 1"
              step="1"
              :tick-labels="isoLabels"
              class="align-center"
            >
              <template v-slot:append>
                <v-text-field
                  v-model="iso"
                  class="mt-0 pt-0"
                  type="number"
                  style="width: 60px"
                ></v-text-field>
              </template>
            </v-slider>
          </v-col>
        </v-row>
      </v-container>
    </v-card-text>
  </v-card>
  </v-container>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component({
  data () {
    return {
      ev: 9,
      tv: 7,
      av: 2,
      iso: 0,
      evLabels: [1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0, 10.0, 11.0, 12.0, 13.0, 14.0],
      tvLabels: [1, 2, 4, 8, 15, 30, 60, 125, 250, 500, 1000, 2000, 4000],
      avLabels: [1.4, 2.0, 2.8, 4.0, 5.6, 8.0, 11, 16, 22, 32],
      isoLabels: [100, 200, 400, 800, 1600, 3200, 6400, 12800]
    }
  },
  computed: {
    // calcTv() {
    //   return this.tv
    // },
    calcAv() {
      console.log(this.ev, this.tv, this.iso)
      return this.ev - this.tv - this.iso
    },
}
})
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;

  }
</script>
