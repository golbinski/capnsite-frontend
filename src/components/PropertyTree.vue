<template>
  <div>
    <div v-for="node in nodes" :key="node.id">
      <div v-if="node.children !== undefined" class="section" :class="{ expanded: node.expanded }">
        <span class="section-label" @click="onSectionClick(node)" @dblclick="onSectionDoubleClick(node)">
          {{ node.label }}
        </span>
        <div class="section-children" v-show="node.expanded">
          <property-tree :nodes="node.children" />
        </div>
      </div>
      <div v-else class="property">
        <span class="property-label" @click="onPropertyClick(node)">
          {{ node.label }}
        </span>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'PropertyTree',
  props: {
    nodes: {
      type: Array,
      required: true
    }
  },
  inject: ['bus'],
  methods: {
    onSectionClick(node) {
      node.expanded = !node.expanded;
    },
    onPropertyClick(node) {
      this.bus.emit('view-properties', node);
    },
    onSectionDoubleClick(node) {
      this.expandRecursive(node, true);
    },
    expandRecursive(node, expand) {
      node.expanded = expand;
      if (node.children !== undefined) {
        for (let i = 0; i < node.children.length; i++) {
          const childNode = node.children[i];
          this.expandRecursive(childNode, expand);
        }
      }
    }
  }
};
</script>

<style>
.section-label,
.property-label {
  cursor: pointer;
}

.section.expanded > .section-label::before {
  content: '-';
  margin-right: 5px;
}

.section > .section-label::before {
  content: '+';
  margin-right: 5px;
}

.property > .property-label::before {
  content: '-';
  margin-right: 5px;
}

.section-children {
  margin-left: 20px;
}
</style>