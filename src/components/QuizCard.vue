<script setup lang="ts">
import { ref } from "vue";

const questions = [
  {
    question: "What is 1 + 1",
    answer: ["2", "3", "6", "7"],
    corrrectAnswer: "2",
  },
  {
    question: "What is 2 * 2",
    answer: ["2", "3", "4", "10"],
    corrrectAnswer: "4",
  },
  {
    question: "What is 105 / 5",
    answer: ["21", "3", "12", "22"],
    corrrectAnswer: "21",
  },
  {
    question: "What is 1 - 1",
    answer: ["None", "1", "-1", "0"],
    corrrectAnswer: "0",
  },
  {
    question: "What is 0 + 9",
    answer: ["10", "19", "9", "8"],
    corrrectAnswer: "9",
  },
];

const score = ref(0);
const selectedQuestion = ref(questions[0]);
const questionCount = ref(1);
const selectedOption = ref("");
const showScore = ref(false);

const submitAnswer = () => {
  console.log("submit");
  if (selectedQuestion.value.corrrectAnswer === selectedOption.value) {
    score.value++;
  }
  if (questionCount.value < questions.length) {
    selectedQuestion.value = questions[questionCount.value];
    questionCount.value++;
    selectedOption.value = "";
  } else {
    showScore.value = true;
  }
};
</script>

<template>
  <div class="wrapper">
    <form @submit.prevent="submitAnswer" v-show="!showScore">
      <div class="questionWrapper">
        <div class="questionText">
          {{ questionCount }}) {{ selectedQuestion.question }}
        </div>
        <div class="option" v-for="(item, i) in selectedQuestion.answer">
          <input
            type="radio"
            name="answers"
            :id="`option${i}`"
            v-model="selectedOption"
            :value="item"
          />
          <label :for="`option${i}`"> {{ item }} </label>
        </div>
      </div>

      <button type="submit">Submit</button>
    </form>
    <div class="score" v-show="showScore">Your Score is {{ score }} out of {{ questions.length }} </div>
  </div>
</template>

<style scoped>
.wrapper {
  height: 300px;
  width: 400px;
  background-color: #fff;
  border-radius: 10px;
}

form {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.questionWrapper {
  flex: 1;
  padding: 1rem;
}

.option > input {
    margin-right: 5px;
}

form > button {
  background-color: black;
  border: none;
  padding: 1rem;
  color: #fff;
  font-size: 16px;
  cursor: pointer;
}

.questionText {
  height: 30px;
}

.option {
  padding: 0.5rem 0;
}

.score {
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>
