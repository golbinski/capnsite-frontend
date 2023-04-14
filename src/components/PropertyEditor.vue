<template>
  <div>
    <h2 v-if="node">{{ node.label }} Properties:</h2>
    <table v-if="node && node.properties">
      <thead>
        <tr>
          <th v-for="key in Object.keys(node.properties)" :key="key">{{ key }}</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td v-for="value in Object.values(node.properties)" :key="value">{{ value }}</td>
        </tr>
      </tbody>
    </table>
    <div v-if="!node">No node selected</div>
  </div>
</template>

<script>

import { inject } from 'vue';

export default {
  name: 'PropertyEditor',
  data() {
    return {
      node: null
    };
  },
  inject: ['bus'],
  mounted() {
    const eventBus = inject('bus');
    eventBus.on('view-properties', property => {
      this.node = property;
    });
  }
};
</script>

<style>
/* Add styles for the properties pane */
</style>