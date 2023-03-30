<template>
  <div>
    <h2 v-if="node">{{ node.label }} Properties:</h2>
    <ul v-if="node && node.properties">
      <li v-for="(value, key) in node.properties" :key="key">
        <strong>{{ key }}:</strong> {{ value }}
      </li>
    </ul>
    <div v-if="!node">No node selected</div>
  </div>
</template>

<script>
export default {
  name: 'PropertyEditor',
  props: {
    node: {
      type: Object,
      default: null
    }
  }
};
</script>

<style>
/* Add styles for the properties pane */
</style>