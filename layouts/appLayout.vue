<template>
  <!-- <appHeader /> -->
  <div class="drrr">
    <label>
      dropdown1-single: <b_dropdown :dropdown="dropdown_1" />
      <br />
      <p>Value:{{}} | Title:{{}}</p>
    </label>
    <label>
      dropdown2-single-null: <b_dropdown :dropdown="dropdown_2" />
      <br />
      <p>Value:{{}} | Title:{{}}</p>
    </label>
    <label>
      dropdown3-single: <b_dropdown :listItems="dropdown_3"/>
      <br />
      <p>Value:{{}} | Title:{{}}</p>
    </label>
    <label>
      dropdown4-single: <b_dropdown :listItems="dropdown_4"/>
      <br />
      <p>Value:{{}} | Title:{{}}</p>
    </label>
  </div>
  <slot />
  <appFooter />
</template>

<script setup lang="ts">
//@ import Components:
import appHeader from '@/components/inc/appHeader.vue';
import b_dropdown from '@/components/BUI/b-dropdown.vue';
import appFooter from '@/components/inc/appFooter.vue';
  

//@ Data:
const dropdown_1 = {
  value:[{ id: 5, title: `hussein_05` }],
  items:[
  {
    id: 1,
    title:
      "hussein_01hussein_01hussein_01hussein_01hussein_01hussein_01hussein_01hussein_01hussein_01hussein_01hussein_01hussein_01hussein_01",
  },
  { id: 2, title: "1111111111222222222233333333333" },
  { id: 3, title: "hussein_03" },
  { id: 4, title: "hussein_04" },
  { id: 5, title: "hussein_05" },
  { id: 6, title: "hussein_06" },
  { id: 7, title: "hussein_07" },
  { id: 8, title: "hussein_08" },
  { id: 9, title: "hussein_09" },
  { id: 10, title: "hussein_10" },
  { id: 11, title: "hussein_11" },
  { id: 12, title: "hussein_12" },
  { id: 13, title: "hussein_13" },
  { id: 14, title: "hussein_14" },
  { id: 15, title: "hussein_15" },
],
  setting:[{isOpen:true},{multiMode:true}],

};



const dropdown_2 = {
  value:[],
  items:[],
  setting:[{multiMode:true}],
};
const dropdown_3 = [
  { id:  1, title: "سيد مكه" },
  { id:  2, title: "محمد نجم" },
  { id:  3, title: "حسين عبدالشافي جودة" },
  { id:  4, title: "محمود" },
  { id:  5, title: "سيف" },
  { id:  6, title: "ذياد" },
  { id:  7, title: "صديق" },
  { id:  8, title: "عبده" },
  { id:  9, title: "احمد" },
  { id: 10, title: "عموري" },
];
const dropdown_4 = [
  { id: 1, title:"1"  },
  { id: 2, title: "2" },
  { id: 3, title: "3" },
];
</script>

<style lang="scss" scoped>
// @use "@/assets/sass/helpers/mixins" as *;
// @use "@/assets/sass/helpers/functions" as *;
.drrr{
  display: flex;
  gap:1em;
  text-align: center;
}
</style>
