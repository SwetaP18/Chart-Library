<template>
  <table>
    <tbody>
      <tr>
       <td :colspan="datasource.children && datasource.children.length ? datasource.children.length*2 : null">
        <div class="node" style="width: 250px !important;border: 1px solid rgba(217, 83, 79, 0.8);
    min-height: 24% !important;margin-right:4px" :id="datasource.id" @click.stop="handleClick(datasource)">
          <slot :node-data="datasource" >
            
            <div class="title" style="padding:5px;height:40px">
              <img :src="datasource.image" style="height:25px;" alt="">
              <!-- <i class="fa fa-users symbol"></i>
              {{ datasource.name }} -->
            </div>
            <div class="content mt-4" style="font-size:20px;padding:5px;height:40px">{{ datasource.name  }}</div>
          </slot>
        </div>
       </td>
      </tr>
      <template v-if="datasource.children && datasource.children.length">
        <tr class="lines">
          <td :colspan="datasource.children.length*2">
            <div class="downLine"></div>
          </td>
        </tr>
        <tr class="lines">
          <td class="rightLine"></td>
         <template v-for="n in (datasource.children.length-1)">
            <td class="leftLine topLine"></td>
            <td class="rightLine topLine"></td>
         </template>
          <td class="leftLine"></td>
        </tr>
        <tr class="nodes">
          <td colspan="2"  v-for="child in datasource.children" :key="child.id">
            <node :datasource="child" :handle-click="handleClick">
              <template v-for="slot in Object.keys($scopedSlots)" :slot="slot" slot-scope="scope">
                <slot :name="slot" v-bind="scope"/>
              </template>
            </node>
          </td>
        </tr>
      </template>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'node',
  props: {
    datasource: Object,
    handleClick: Function
  },
  methods: {
  }
};
</script>

<style>
</style>
