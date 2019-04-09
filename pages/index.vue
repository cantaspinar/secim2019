<template>
  <div class="main">
    <v-layout justify-center column>
      <v-flex xs12>
        <v-switch
          v-model="isDifferenceMap"
          class="mb-4"
          label="Fark Haritası"
          color="red"
          hide-details
        ></v-switch>
      </v-flex>
      <v-flex v-if="isDifferenceMap" xs12>
        <v-slider v-model="differencePercentageRate" :thumb-label="true"></v-slider>
      </v-flex>
    </v-layout>
    <Map
      :results="sortedData"
      :isDifferenceMap="isDifferenceMap"
      :differencePercentageRate="differencePercentageRate"
    />
  </div>
</template>

<script>
import Map from "~/components/Map.vue";
import data from "~/assets/secim.json";

export default {
  components: {
    Map
  },
  data() {
    return {
      data,
      sortedData: [],
      isDifferenceMap: false,
      differencePercentageRate: 15
    };
  },

  asyncData() {
    data.forEach(function(element) {
      element.results.sort(function(a, b) {
        return b.voteCount - a.voteCount;
      });
    });
    return {
      sortedData: data
    };
  },
  methods: {}
};
</script>
