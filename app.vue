<template>
  <div id="app">
    <appLayout>
      <NuxtPage />
    </appLayout>

    <div class="fff">
      <i @click="ssg.dark =!ssg.dark">
        <svg v-if="ssg.dark" xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><path fill="currentColor" d="M12 15q1.25 0 2.125-.875T15 12q0-1.25-.875-2.125T12 9q-1.25 0-2.125.875T9 12q0 1.25.875 2.125T12 15m0 2q-2.075 0-3.537-1.463T7 12q0-2.075 1.463-3.537T12 7q2.075 0 3.538 1.463T17 12q0 2.075-1.463 3.538T12 17m-7-4H1v-2h4zm18 0h-4v-2h4zM11 5V1h2v4zm0 18v-4h2v4zM6.4 7.75L3.875 5.325L5.3 3.85l2.4 2.5zm12.3 12.4l-2.425-2.525L17.6 16.25l2.525 2.425zM16.25 6.4l2.425-2.525L20.15 5.3l-2.5 2.4zM3.85 18.7l2.525-2.425L7.75 17.6l-2.425 2.525zM12 12"/></svg>
        <svg v-else xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><path fill="currentColor" d="M12.058 20q-3.334 0-5.667-2.333Q4.058 15.333 4.058 12q0-3.038 1.98-5.27Q8.02 4.5 10.942 4.097q.081 0 .159.006t.153.017q-.506.706-.801 1.57q-.295.865-.295 1.811q0 2.667 1.866 4.533q1.867 1.867 4.534 1.867q.952 0 1.813-.295q.862-.295 1.548-.801q.012.075.018.153q.005.078.005.158q-.384 2.923-2.615 4.904T12.057 20m0-1q2.2 0 3.95-1.213t2.55-3.162q-.5.125-1 .2t-1 .075q-3.074 0-5.237-2.162T9.158 7.5q0-.5.075-1t.2-1q-1.95.8-3.163 2.55T5.058 12q0 2.9 2.05 4.95t4.95 2.05m-.25-6.75"/></svg>
      </i>
      <i @click="ssg.lang = (ssg.lang != 'en')&&'en'||'ar'">
        <svg v-if="ssg.lang == 'en'" xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><g fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"><path d="M3 12a5 5 0 0 1 5-5h8a5 5 0 0 1 0 10H8a5 5 0 0 1-5-5"/><path d="M18.5 12a2.5 2.5 0 1 1-5 0a2.5 2.5 0 0 1 5 0"/></g></svg>
        <svg v-else xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><g fill="none" stroke="var(--c30)" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"><path d="M21 12a5 5 0 0 0-5-5H8a5 5 0 0 0 0 10h8a5 5 0 0 0 5-5"/><path d="M5.5 12a2.5 2.5 0 1 0 5 0a2.5 2.5 0 0 0-5 0"/></g></svg>
      </i>
    </div>
  </div>
</template>

<script setup lang="ts">
//@ import Components:
import appLayout from '@/layouts/appLayout.vue';

//@ import Libraries:
import { defineProps, ref, defineEmits, onMounted, onBeforeUnmount } from "vue";

//@ props:
const props = defineProps({
  // title:{type: String,required: true,default:'BomBa' }
});

//@ Emits:
const emits = defineEmits(['handleClick'])

//@ Data:
const ssg = ref({dark: false,lang:'en'});

//@ watch:
watch(
  ()=>ssg.value.dark,
  (nv) => {
    document.getElementsByTagName('html')[0]
    .classList.replace((!nv && `dark`) || `light`, (nv && `dark`) || `light`);
  },
  { deep: true }
);
watch(
  ()=>ssg.value.lang,
  (nv) => {
    document.getElementsByTagName('html')[0]
    .dir = (nv == 'en')&&'ltr'||'rtl';
  },
  { deep: true }
);

//@ Method:
// useHead({htmlAttrs: { class: (ssg.dark && `dark`) || `light` },}); /* note: i use this in [app.vue,error.vue,] */
useHead({htmlAttrs: { class: (ssg.value.dark && `dark`) || `light` },}); /* note: i use this in [app.vue,error.vue,] */
</script>

<style lang="scss" scoped>
// @use "@/assets/sass/helpers/mixins" as *;
// @use "@/assets/sass/helpers/functions" as *;

.fff{
  padding: .4em 0;
  color:$c60;
  font-size: 300%;
  line-height: 0;
  text-align: center;
  cursor: pointer; 
  background-color: $c10;

  display: flex;
  flex-wrap: row nowrap;
  justify-content: center;
  align-items: center;
  gap: 0.4em;
}
</style>
