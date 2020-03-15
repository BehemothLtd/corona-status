<template>
  <div class="clash-card archer">
    <div class="clash-card__image clash-card__image--archer">
      <img
        class="country-symbol"
        :src="countryImg"
      />
    </div>
    <div class="clash-card__level clash-card__level--archer">

    </div>
    <div class="clash-card__unit-name">{{ countryData.Country_Region }}</div>
    <div
      class="clash-card__unit-description"
    >
      {{ countryData.Confirmed }} Cases
    </div>

    <div class="clash-card__unit-stats clash-card__unit-stats--archer clearfix">
      <div class="one-third">
        <div class="stat">{{ countryData.Active }}</div>
        <div class="stat-value">Active</div>
      </div>

      <div class="one-third">
        <div class="stat">{{ countryData.Deaths }}</div>
        <div class="stat-value">Deaths</div>
      </div>

      <div class="one-third">
        <div class="stat">{{ countryData.Recovered }}</div>
        <div class="stat-value">Recovered</div>
      </div>
    </div>
  </div>
</template>

<script>
import { getCountryImg } from '../functions.js';

export default {
  props: {
    countryData: {
      type: Object,
      required: true
    }
  },
  data: function() {
    return {
      countryImg: null
    }
  },
  created: function() {
    this.countryImg = getCountryImg(this.countryData.Country_Region);
  }
};
</script>