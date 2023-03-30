<template>
  <div>
    <h1>Tree Structure</h1>
    <div class="property-tree-pane">
      <PropertyTree :nodes="treeData" />
    </div>
    <div class="properties-pane">
      <PropertyEditor :node="propertiesNode" @viewProperties="onViewProperties($event)" />
    </div>
  </div>
</template>

<script>
/* eslint-disable vue/no-unused-components */

import PropertyTree from '@/components/PropertyTree.vue';
import PropertyEditor from '@/components/PropertyEditor.vue';

export default {
  name: 'CapnSite',
  components: {
    PropertyTree,
    PropertyEditor
  },
  methods: {
    onViewProperties(node) {
      this.propertiesNode = node;
    }
  },
  data() {
    return {
      propertiesNode: null,
      treeData: [
        {
          id: '446fes6',
          label: 'static',
          children: [
            {
              id: '9c5f5d5',
              label: 'sor_venues',
              children: [
                {
                  id: '9dd81ff',
                  label: 'LSE',
                  properties: {
                    market_segments: {
                      one_to_many: '9c5f5d6',
                      value: [],
                      mutable: true
                    }
                  }
                },
                {
                  id: '9c5f7d5',
                  label: 'PAR',
                  properties: {}
                },
                {
                  id: '9c5f8d5',
                  label: 'ISE',
                  properties: {}
                }
              ]
            }
          ]
        },
        {
          id: '3442abc',
          label: 'external',
          children: [
            {
              id: '9c5f5d6',
              label: 'mifid_market_segments',
              children: [
                {
                  id: '9c5f5d8',
                  label: "XBRU/XBRU",
                  properties: {
                    operating_mic: "XBRU",
                    segment_mic: "XBRU",
                    market_name: "EURONEXT BRUSSELS"
                  }
                },
                {
                  id: '9c5f5d9',
                  label: "XDUB/EDBG",
                  properties: {
                    operating_mic: "XDUB",
                    segment_mic: "EDBG",
                    market_name: "EURONEXT IRELAND"
                  }
                },
                {
                  id: '9c5f5d1',
                  label: "XSTO/DOSE",
                  properties: {
                    operating_mic: "XSTO",
                    segment_mic: "DOSE",
                    market_name: "NORDIC@MID"
                  }
                },
                {
                  id: '9c3f5d5',
                  label: "XPAR/XETF",
                  properties: {
                    operating_mic: "XPAR",
                    segment_mic: "XETF",
                    market_name: "EURONEXT ETF PARIS"
                  }
                }
              ]
            }
          ]
        }
      ]
    };
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
