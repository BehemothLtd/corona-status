<template>
  <div>
    <DashboardCountryStatus
      v-for="countryDatum in countryData"
      :key="countryDatum.OBJECTID"
      :country-data="countryDatum"
    />
  </div>
</template>

<script>
import DashboardCountryStatus from "./DashboardCountryStatus";

export default {
  components: {
    DashboardCountryStatus
  },
  props: {
    countryData: {
      type: Array,
      required: true
    }
  }
};
</script>

<style>
</style>