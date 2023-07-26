
<script setup>

import {computed, defineProps} from "vue";
const props=defineProps(['totalResults','totalCorrectAnswer'])


let resultIndex=computed(()=>{
  let index=0;
  props.totalResults.forEach((e,i)=>{
    if (e.min<=props.totalCorrectAnswer && e.max>=props.totalCorrectAnswer){
      index=i;
    }
  });
  return index;
})

</script>


<template>
  <div class="result">
    <div class="title">{{ totalResults[resultIndex].title }}</div>
    <div class="desc">{{ totalResults[resultIndex].desc }}</div>
  </div>
</template>


<style scoped>

</style>