<template>
  <div class="card-item">
    <div class="clash-card">
      <div class="clash-card__image clash-card__image--archer">
        <img class="country-symbol" src="https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/ff44d2b7-ee16-46f4-b237-85abbcc4cc08/d3nq3tn-93d1f4a1-fdee-418f-9be8-87055ce0ff3c.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7InBhdGgiOiJcL2ZcL2ZmNDRkMmI3LWVlMTYtNDZmNC1iMjM3LTg1YWJiY2M0Y2MwOFwvZDNucTN0bi05M2QxZjRhMS1mZGVlLTQxOGYtOWJlOC04NzA1NWNlMGZmM2MucG5nIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmZpbGUuZG93bmxvYWQiXX0.4nFIc8QDHtdRQHVwXU8ArpEbKV2uPaC-w5tHIeejkjg" />
      </div>
      <div class="clash-card__level clash-card__level--archer"></div>
      <div class="clash-card__unit-name">{{ countryData.Country_Region }}</div>
      <div class="clash-card__unit-description">{{ countryData.Confirmed }} Cases</div>

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
  </div>
</template>

<script>
import { getCountryImg } from "../functions.js";

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
    };
  },
  created: function() {
    this.countryImg = getCountryImg(this.countryData.Country_Region);
  }
};
</script>
