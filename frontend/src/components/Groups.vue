<template lang="html">
  <div class="columns is-multiline">
    <div class="column is-3" v-for="(countries, group) in groups" :key="group">
      <div class="group">
        <h3 class="title">Group {{ group }}</h3>
        <ul>
          <li
            v-for="(country, idx) in countries"
            :key="idx"
            :class="{ 'out' : country.eliminated }"
          >
            {{ country.name }} <small>(ranking: {{ country.ranking }})</small><br />
            <small v-if="country.user"><strong>{{ country.user }}</strong></small>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'groups',
  data() {
    return {
      groups: {},
    };
  },
  mounted() {
    axios.get('/static/teams.json')
      .then((response) => {
        this.groups = response.data.collection.reduce((groups, country) => {
          const newGroups = groups;
          if (country.group in groups) {
            newGroups[country.group].push(country);
          } else {
            newGroups[country.group] = [country];
          }
          return newGroups;
        }, {});
      });
  },
};
</script>
