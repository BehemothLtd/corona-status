<template>
  <div>
    <Loading v-if="loading" />
    <DashboardCountryList v-else :country-data="countryBaseData" />
  </div>
</template>

<script>
import axios from "axios";

import DashboardCountryList from "./DashboardCountryList";
import Loading from "./Loading";

const API_ENDPOINT =
  "https://services1.arcgis.com/0MSEUqKaxRlEPj5g/arcgis/rest/services/ncov_cases/FeatureServer/2/query?f=json&where=Confirmed%20%3E%200&returnGeometry=false&spatialRel=esriSpatialRelIntersects&outFields=*&orderByFields=Confirmed%20desc&outSR=102100&resultOffset=0&resultRecordCount=100&cacheHint=true&fbclid=IwAR3WOSOjHOo31y7U4vctHZ_vn_gC-58UrU3vwRuCNpcawt0Lk9MPuQ0bLOc";

export default {
  components: {
    DashboardCountryList,
    Loading
  },
  data: function() {
    return {
      loading: true,
      countryBaseData: []
    };
  },
  created: async function() {
    await this.fetchData();

    console.log(this.countryBaseData.map(c => c.Country_Region));
  },
  methods: {
    fetchData: async function() {
      const response = await axios.get(API_ENDPOINT);
      this.loading = false;

      this.countryBaseData = response.data.features.map(i => i.attributes);
    }
  }
};
</script>
