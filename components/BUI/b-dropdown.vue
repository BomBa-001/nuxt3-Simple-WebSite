<template>
  <div class="BUI">
    <div class="dropdown" tabindex="0" 
    @blur="toggleOpen = false">
      <div
        :class="['select', { 'select-clicked': toggleOpen }]"
        @click="toggleOpenMenu()"
      >
      <!-- <input type="text" id="" value="itemSelected.title" placeholder="??????"> -->
        <!-- إيس مكتبة خارجية titleتعديل ال -->
        <span
      v-if="itemSelected.id && false"
          :id="itemSelected.id"
          class="selected"
          :title="itemSelected.title"
          >555{{ itemSelected.title }}
          <!-- {{ itemSelected.title.substring(0, 10).concat(" ...") }} -->
        </span>
        <span
          v-else-if="true"
          class="selected"
          >
          <i
          v-for="(item, i) in itemSelected"
          :key="i"
          :id="item.id"
          :title="item.title"
          class="selected__i"
          >{{ item.title }}
            <b class="delete"
            @click="toggleOpenMenu(); itemSelected=itemSelected.filter(a=>a.id!=item.id);"
            ><svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><path fill="currentColor" d="m9.4 16.5l2.6-2.6l2.6 2.6l1.4-1.4l-2.6-2.6L16 9.9l-1.4-1.4l-2.6 2.6l-2.6-2.6L8 9.9l2.6 2.6L8 15.1zM7 21q-.825 0-1.412-.587T5 19V6H4V4h5V3h6v1h5v2h-1v13q0 .825-.587 1.413T17 21z"/></svg></b>
        </i>
        </span>
        <i
          v-if="itemSelected.id"
          class="clear"
          @click="itemSelected = { id: '', title: '' };
          toggleOpenMenu()"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="1em"
            height="1em"
            viewBox="0 0 16 16"
          >
            <path
              fill="currentColor"
              d="M2.75 2a.5.5 0 0 0-.485.379l-.25 1a.5.5 0 1 0 .97.242L3.14 3h2.723l-1.4 8h-.736a.5.5 0 0 0 0 1h2.295a5.571 5.571 0 0 1 0-1h-.544l1.4-8H9.86l-.095.379a.5.5 0 1 0 .97.242l.25-1A.5.5 0 0 0 10.5 2zM1.5 13h4.707c.099.349.23.683.393 1H1.5a.5.5 0 0 1 0-1M16 11.5a4.5 4.5 0 1 1-9 0a4.5 4.5 0 0 1 9 0m-2.646-1.146a.5.5 0 0 0-.708-.708L11.5 10.793l-1.146-1.147a.5.5 0 0 0-.708.708l1.147 1.146l-1.147 1.146a.5.5 0 0 0 .708.708l1.146-1.147l1.146 1.147a.5.5 0 0 0 .708-.708L12.207 11.5z"
            />
          </svg>
        </i>
        <i :class="['caret', { 'caret-rotate': toggleOpen }]"></i>
      </div>
      <ul :class="['menu', { 'menu-open': toggleOpen }]">
        <li
          v-for="(item, i) in items"
          :key="i"
          :id="item.id"
          :class="[{ active: item.id == itemSelected.id }]"
          @click="toggleSelected(item)"
          @dblclick="toggleOpenMenu()"
        >
          {{ item.title }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
//@ import Libraries:
import { defineProps, ref, defineEmits, onMounted, onBeforeUnmount } from "vue";

//@ props:
const props = defineProps({
  // title:{type: String,required: true,default:'BomBa' }

    dropdown: {type: Object,default: {
      value:[{ id: '', title: '', },],
      items:[],
      setting:[{isOpen:false},{searchText:false},{multiMode:false}],
    }},
  });
//@ Emits:
const emits = defineEmits(['handleChing'])

//@ Data:
// (props.dropdown.setting[0].searchText || false)
// (props.dropdown.setting[0].multiMode || false)
const itemSelected = ref(props.dropdown.value);
const toggleOpen = ref(props.dropdown.setting[0].isOpen || false);
const Mode = ref(props.dropdown.setting[0].multiMode || false);
// const itemSelected = ref({ id: 5, title: "hussein_05" });


//@ computed:
const items = computed(() => props.dropdown.items.filter(i => i));

//@ Function:
const toggleOpenMenu = (e) => {
  toggleOpen.value = !toggleOpen.value;
};
const toggleSelected = (e) => {
  // console.log(Mode.value);
  // if (Mode.value)
  if (true){
  // itemSelected.value.append(e);
  itemSelected.value.push(e);
  console.log(itemSelected.value);}
  else itemSelected.value = e;
};
// deleted_itemSelected= (id)=>{
//   console.log(id);
//   console.log(itemSelected.value);
  
//   itemSelected.value=itemSelected.value.filter(a=>a.id!=id);

// }

//@ Mounted:
// const dropdown = ref(null);
onMounted(() => {
  // console.log(props);

//   dropdown.value.addEventListener('click', e=> console.log(dropdown.value))
//   dropdown.value.addEventListener('blur', e=> console.log('blur'))
//   dropdown.value.addEventListener('focus', e=> console.log('focus'))
//   // dropdown.value.addEventListener('blur', e=> toggleOpenMenu())
//   // document.addEventListener('blur', e=> toggleOpenSS())
})
</script>

<style lang="scss" scoped>
@use "@/assets/sass/helpers/mixins" as *;
@use "@/assets/sass/helpers/functions" as *;

.BUI {
  --width: 15em;

  // --ctext: #fff;
  --cbg: #{$c60};//#121212;//#2a2f3b;
  --cbr: #{$c60-l02};//#2a2f3b;//#2a2f3b;
  --cbg-hover: #{$c60-l02};//#efefef;
  --cbox-shadow:#{$c30};//#26489a;
  --ccaret: var(--cbr);//#fff;
  --ccaret-hover: var(--ctext);//#fff;
  --cbg-menu: var(--cbg);//#323741;
  --cbr-menu:var(--cbr);//#2a2f3b;
  --cbox-shadow-menu: #{$c30-a02};//hsla(0, 0%, 0%, 0.4); //#00000033;
  --cbg-menu-li:#{$c60-l05};// #2a2f3b;
  // --cdanger:hsl(0, 86%, 59%);
  // font-family: sans-serif;
  width: fit-content;

  display: flex;
  justify-content: center;
  align-items: center;
  flex-flow: row nowrap;

  position: relative;
  word-wrap: normal;

  @extend .outline-none;
  @extend .unselect-text;
  // --- --- --- --- --- --- --- --- --- --- --- --- --- --- ---
  .dropdown {
    width: var(--width);
    min-width: 5em;
    position: relative;
    // -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    * {
      box-sizing: border-box;
    }
  }
  // --- --- --- --- --- --- --- --- --- --- --- --- --- --- ---
  .select {
    padding: 0 1em;
    cursor: pointer;
    height: 2.5em;
    color: var(--ctext);
    background: var(--cbg);
    border: 0.125em solid var(--cbr);
    border-radius: 0.5em;

    display: flex;
    justify-content: flex-end;
    align-items: center;
    gap: 0.8em;

    overflow: hidden;

    transition: background 0.3s;
    // -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    &:hover {
      background: var(--cbg-hover)
    }
    &:hover .caret{border-block-start-color: var(--ccaret-hover);}
    // -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    &-clicked {
      // clicked styles (added later in javascript)
      border: 2px solid var(--cbr);
      box-shadow: 0 0 0.4em var(--cbox-shadow);
    }
  }
  // --- --- --- --- --- --- --- --- --- --- --- --- --- --- ---
  .selected {
    flex-grow: 1;
    overflow: hidden;
    font-size: 80%;

    display: flex;
    flex-flow: row nowrap;
    justify-content: center;
    align-items: center;
    height: 100%;
    gap: 0.5em;

    @extend .scrollbar;
    
    

    &__i{
      padding: 0.1em 0.5em;
      // background: chsla(c60, $l:   10%,$ql:'-');
      border-radius: 1em;
      font-size: 100%;
      text-align: start;
      box-shadow: 0 0 0.2em var(--cbr);

      display: flex;
      flex-flow: row now;
      justify-content: center;
      align-items: center;
      gap: 0.5em;

      .delete{
        color:var(--cbr);
        position: relative;
        inset-block-start: -0.125em;
        @extend %changeCursor;
        
      }:hover{color:var(--cdanger);}
    }
  }
  .clear svg {
    color: var(--cwarning);
    @extend %changeCursor;
  }
  .caret {
    border-inline-start: 0.4125em solid transparent;
    border-inline-end: 0.4125em solid transparent;
    border-block-start: 0.575em solid var(--ccaret);
    transition: 0.3s;
    // -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    &-rotate {
      // rotate styles (added later in javascript)
      rotate: 180deg;
    }
  }

  // --- --- --- --- --- --- --- --- --- --- --- --- --- --- ---
  .menu {
    padding: 0.2em 0.5em;
    display: none; //none | flex
    width: 100%;
    max-height: 20em;
    // color: var(--ctext-menu);//--ctext-menu:#9fa5b5;
    color: var(--ctext);//--ctext-menu:#9fa5b5;
    opacity: 75%;
    background: var(--cbg-menu);
    border: 1px solid var(--cbr-menu);
    border-radius: 0.5em;
    box-shadow: 0 0.5em 1em var(--cbox-shadow-menu);
    list-style: none;
    position: absolute;
    inset-block-start: 2.8em;
    inset-inline-start: 0;

    // display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;

    @extend .scrollbar-y;


    transition: all 0.2s ease-in-out 0s;
    z-index: 1;

    // -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --

    li {
      padding: 0.7em 0.5em;
      padding-inline-end: 3.5em ;
      margin: 0.3em 0;
      // width: inherit;
      border-radius: 0.5em;
      cursor: pointer;
      // opacity: 0.6;
    height: 2.5em;

      @extend .scrollbar-x;
      // overflow-x: hidden;
      transition: all 0.2s ease-in-out 0s;
      // - - - - - - - - - - - - - - - - - - - - - - - - - - - -
      &:hover,
      &.active {
        background: var(--cbg-menu-li);
      }
    }
    // -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
    &-open {
      // open styles (added later in javascript)
      display: flex;
      opacity: 1;
    }
  }
}

%changeCursor{cursor: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="1.3em" height="1.4em" viewBox="0 0 448 512"><path fill="hsl(0, 86%, 59%)" d="M160 64c0-8.8 7.2-16 16-16s16 7.2 16 16v136c0 10.3 6.6 19.5 16.4 22.8s20.6-.1 26.8-8.3c3-3.9 7.6-6.4 12.8-6.4c8.8 0 16 7.2 16 16c0 10.3 6.6 19.5 16.4 22.8s20.6-.1 26.8-8.3c3-3.9 7.6-6.4 12.8-6.4c7.8 0 14.3 5.6 15.7 13c1.6 8.2 7.3 15.1 15.1 18s16.7 1.6 23.3-3.6c2.7-2.1 6.1-3.4 9.9-3.4c8.8 0 16 7.2 16 16V392c0 39.8-32.2 72-72 72H211.4c-37.4 0-72.4-18.7-93.2-49.9L50.7 312.9c-4.9-7.4-2.9-17.3 4.4-22.2s17.3-2.9 22.2 4.4l38.7 58.1c5.9 8.8 16.8 12.7 26.9 9.7s17-12.4 17-23V64zm16-64c-35.3 0-64 28.7-64 64v197.7c-20.8-23.7-56.5-28.9-83.5-11c-29.4 19.7-37.4 59.4-17.7 88.8l67.5 101.3C108 485.3 157.9 512 211.4 512H328c66.3 0 120-53.7 120-120V272c0-35.3-28.7-64-64-64c-4.5 0-8.8.5-13 1.3c-11.7-15.4-30.2-25.3-51-25.3c-6.9 0-13.5 1.1-19.7 3.1c-11.6-16.4-30.7-27.1-52.3-27.1c-2.7 0-5.4.2-8 .5V64c0-35.3-28.7-64-64-64m48 304c0-8.8-7.2-16-16-16s-16 7.2-16 16v96c0 8.8 7.2 16 16 16s16-7.2 16-16zm48-16c-8.8 0-16 7.2-16 16v96c0 8.8 7.2 16 16 16s16-7.2 16-16v-96c0-8.8-7.2-16-16-16m80 16c0-8.8-7.2-16-16-16s-16 7.2-16 16v96c0 8.8 7.2 16 16 16s16-7.2 16-16z"/></svg>') 4 4, pointer;}
.light{.dropdown .select .selected__i{ background: chsla(c60, $l:   10%,$ql:'-');}}
.dark{.dropdown .select .selected__i{ background: chsla(c60, $l:   30%,$ql:'+');}}

</style>
