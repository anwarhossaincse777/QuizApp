
<script setup>
import { defineProps,defineEmits } from 'vue';
const props=defineProps(["allQuestions","questionsAllAnswered"])

const emit=defineEmits(["question-answered"])


const selectAnswer = (is_correct) => {
  emit("question-answered",is_correct)
}

</script>


<template>
  <div class="questions-ctr">
    <div class="progress">
      <div class="bar"   :style="{ width: `${(questionsAllAnswered / allQuestions.length) * 100}%` }">

      </div>
      <div class="status">
        {{ questionsAllAnswered }} out of {{ allQuestions.length }} questions answered
      </div>
    </div>
    <transition-group name="fade">
      <div   class="single-question"
      v-for="(question,index) in allQuestions" :key="question.q"
             v-show="questionsAllAnswered === index"
      >
        <div class="question">
            {{question.q}}
        </div>


        <div class="answers">
          <div  @click="selectAnswer(answersItem.is_correct)" class="answer" v-for="answersItem in question.answers" :key="answersItem.text">
            {{answersItem.text}}
          </div>

        </div>
      </div>

    </transition-group>
  </div>
</template>



<style scoped>

</style>