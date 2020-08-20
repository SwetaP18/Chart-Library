<template>
  <div id="app">
    <org-chart :datasource="ds" style="width:100%;height:100%" @node-click="selectNode">
<!--       <template slot-scope="{ nodeData }">
        <b @click="selectNode(nodeData)">{{ nodeData.name }}</b>
      </template> -->
    </org-chart>
  </div>
</template>

<script>
import OrgChart from './components/OrganizationChartContainer.vue'

export default {
  name: 'app',
  components: {
    OrgChart
  },
  data () {
    return {
      ds: {},
      image: require('./images/icon1.png')
    }
  },
  mounted () {
      this.ds = { 
        'id': '1',
        'name': 'Title 1',
        'image':this.image,
        'children': [
          { 'id': '2', 'name': 'Title 2','image':this.image,},
          { 'id': '3', 'name': 'Title 3','image':this.image,
            'children': [
              { 'id': '4', 'name': 'Title 4','image':this.image,},
              { 'id': '5', 'name': 'Title 5','image':this.image,
                'children': [
                  { 'id': '6', 'name': 'Title 6','image':this.image,},
                  { 'id': '7', 'name': 'Title 7','image':this.image,}
                ]
               }
             ]
           },
          { 'id': '8', 'name': 'Title 8','image':this.image,},
          { 'id': '9', 'name': 'Title 9','image':this.image,}
        ]
      }
    },
  methods: {
    selectNode (nodeData) {
      alert('node ' + nodeData.name + ' is selected')
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
