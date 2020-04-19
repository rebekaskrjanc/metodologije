<template>
  <div id="app">

    <h1>Participatory design methodologies</h1>
    <div class="header-line"></div>
    
    <div class="questionnaire-container">

      <div v-if="questionnaireStep !== 0" class="back-btn" @click="goStepBack()">
        <img class="previous-btn-icon" src="./assets/back.svg">
        <span class="previous-btn">Previous question</span>
      </div>

      <div v-if="questionnaireStep === 0">
        <h2>{{step0.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step0.answers" :key="index">
              <div class="answer" @click="setQuestionnaireStep(index)">{{index+1}}. {{answer}}</div>
          </div>
        </div>
      </div>

      <div v-if="questionnaireStep === 1">
        <h2>{{step1.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step1.answers" :key="index">
            <div class="answer" @click="setQuestionnaireStep(index)">{{index+1}}. {{answer}}</div>
          </div>
        </div>
      </div>

      <div v-if="questionnaireStep === 2">
        <h2>{{step2.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step2.answers" :key="index">
            <div class="answer" @click="setQuestionnaireStep(index)">{{index+1}}. {{answer}}</div>
          </div>
        </div>
      </div>

      <div v-if="questionnaireStep === 3">
        <h2>{{step3.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step3.answers" :key="index">
            <div class="answer" @click="setQuestionnaireStep(index)">{{index+1}}. {{answer}}</div>
          </div>
        </div>
      </div>

      <div v-if="questionnaireStep === 3.1">
        <h2>{{step3_1.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step3_1.answers" :key="index">
            <div class="answer" @click="setQuestionnaireStep(index)">{{index+1}}. {{answer}}</div>
          </div>
        </div>  
      </div>

      <div v-if="questionnaireStep === 3.2">
        <h2>{{step3_2.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step3_2.answers" :key="index">
            <div class="answer" @click="setQuestionnaireStep(index)">{{index+1}}. {{answer}}</div>
          </div>
        </div>
      </div>
    </div>

    <div class="finalAnswer" v-if="finalAnswer">You should use <span class="methodology">{{finalAnswer}}</span></div>

  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      previousStep: 0,
      questionnaireStep: 0,
      finalAnswer: null,
      step0: { // first question
        question: "Which project phase are you currently in?",
        answers: [
          "Project Initiation",
          "Project Planing",
          "Project Execution",
          "Project Performance",
          "Project Closure"
        ]
      },
      step1: { // Project Initiation
        question: "You found the problem you will be solving and:",
        answers: [
          "You need to find the right solution for it.",
          "You have the appropriate solution in mind but you need some inovative ideas which will  bring additional value to the project."
        ]
      },
      step2: { // Project Planing
        question: "You need to:",
        answers: [
          "Raise capital or outsource part of your work.",
          "Come up with additional ideas for setting goals.",
          "Clarification is needed."
        ]
      },
      step3: { // Project Execution
        question: "Did you make a product prototype?",
        answers: [
          "No",
          "Yes"
        ]
      },
      step3_1: { // Project Execution NO
        question: "You need:",
        answers: [
          "To find the best (holistic) solution",
          "Help with prioritizing ideas in order to determine a course of action",
          "To better define the interaction between the user and a system",
          "To come up with fresh ideas",
          "Determine parts of the product (e.g. colours) and it’s functionalities.",
          "A cheap way to get a great insight into user’s minds.",
          "To solve a problem involving human factors."
        ]
      },
      step3_2: { // Project Execution NO
        question: "You want to:",
        answers: [
          "Better define the interaction between a user and a system",
          "Definine and solve problems, come up with fresh ideas",
          "Get a feel for the flow of users' experiences",
          "Determine parts of the product (e.g. colours) and it’s functionalities.",
          "See how users interact with the prototype.",
          "Find a cheap way to get a great insight into user’s minds.",
          "Solve a problem involving human factors."
        ]
      },
    }
  },
  methods: {
    setQuestionnaireStep(answerId) {
      switch (this.questionnaireStep) {
        case 0:
          this.setQuestionnaireStepFrom0(answerId);
          break;
        case 1:
          this.setQuestionnaireStepFrom1(answerId);
          break;
        case 2:
          this.setQuestionnaireStepFrom2(answerId);
          break;
        case 3:
          this.setQuestionnaireStepFrom3(answerId);
          break;
        case 3.1:
          this.setQuestionnaireStepFrom3_1(answerId);
          break;
        case 3.2:
          this.setQuestionnaireStepFrom3_2(answerId);
          break;
        case 4:
          this.finalAnswer = "odgovor za cetrtega";
          break;
        case 5:
          this.finalAnswer = "odgovor za petega";
          break;
      }
    },
    setQuestionnaireStepFrom0(answerId) {
      switch (answerId) {
        case 0:
          this.previousStep = this.questionnaireStep;
          this.questionnaireStep = 1;
          break;
        case 1:
          this.previousStep = this.questionnaireStep;
          this.questionnaireStep = 2;
          break;
        case 2:
          this.previousStep = this.questionnaireStep;
          this.questionnaireStep = 3;
          break;
        case 3:
          this.previousStep = this.questionnaireStep;
          this.questionnaireStep = 4;
          break;
      }
    },
    setQuestionnaireStepFrom1(answerId) { // Project Initiation
      switch (answerId) {
        case 0:
          this.finalAnswer = "WCaffe";
          break;
        case 1:
          this.finalAnswer = "Brainstorming";
          break;
      }
    },
    setQuestionnaireStepFrom2(answerId) { // Project Initiation
      switch (answerId) {
        case 0:
          this.finalAnswer = "Crowdsourcing";
          break;
        case 1:
          this.finalAnswer = "Brainstorming";
          break;
        case 2:
          this.finalAnswer = "Five whys";
          break;
      }
    },
    setQuestionnaireStepFrom3(answerId) { // Project Execution v1
      switch (answerId) {
        case 0:
          this.previousStep = this.questionnaireStep;
          this.questionnaireStep = 3.1;
          break;
        case 1:
          this.previousStep = this.questionnaireStep;
          this.questionnaireStep = 3.2;
          break;
      }
    },
    setQuestionnaireStepFrom3_1(answerId) { // Project Execution v1
      switch (answerId) {
        case 0:
          this.finalAnswer = "Crowd contest";
          break;
        case 1:
          this.finalAnswer = "Crowd voting";
          break;
        case 2:
          this.finalAnswer = "User stories";
          break;
        case 3:
          this.finalAnswer = "Brainstorming";
          break;
        case 4:
          this.finalAnswer = "Collage";
          break;
        case 5:
          this.finalAnswer = "Interview";
          break;
        case 6:
          this.finalAnswer = "Five Whys";
          break;
      }
    },
    setQuestionnaireStepFrom3_2(answerId) { // Project Execution v1
      switch (answerId) {
        case 0:
          this.finalAnswer = "User stories";
          break;
        case 1:
          this.finalAnswer = "Brainstorming";
          break;
        case 2:
          this.finalAnswer = "Storyboards";
          break;
        case 3:
          this.finalAnswer = "Collage";
          break;
        case 4:
          this.finalAnswer = "Behavioral mapping";
          break;
        case 5:
          this.finalAnswer = "Interview";
          break;
        case 6:
          this.finalAnswer = "Five Whys";
          break;
      }
    },
    goStepBack() {
      this.questionnaireStep = this.previousStep;
      this.finalAnswer = null;
      if(this.previousStep === 3) {
        this.previousStep = 0;
      }
    }
  }
}
</script>

<style>
html {
  background: #EEEBE8;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #333745;
  padding: 20px;
  max-width: 100vw;
  overflow-x: hidden;
  padding-bottom: 150px;
}

h1 {
  text-align: left;
  font-size: 1.8em;
  margin-bottom: 10px;
  color: #D55F8F;
}

h2 {
  margin-bottom: 30px;
}

.header-line {
  width: 100%;
  height: 3px;
  background: #D5CCCC;
}

.questionnaire-container {
  margin-top: 100px;
}

.answer {
  margin-bottom: 18px;
  font-size: 18px;
  cursor: pointer;
  text-align: left;

  float: left;
  position: relative;
  left: -50%;
  padding: 0px 12px;
}

.answer:hover {
  color: #bd537e;
}

.answer-container {
  float: left;
  position: relative;
  left: 50%;
}

.finalAnswer {
  background-color: #333745;
  position: fixed;
  bottom: 0px;
  color: #D5CCCC;
  text-align: center;
  min-width: calc(100vw - 60px);
  border-radius: 20px 20px 0 0;
  padding: 40px 4px;
  font-size: 24px;
  font-weight: 600;
}

.methodology {
  color: #e3689a;
}

.previous-btn {
  display: inline-block;
  line-height: 20px;
  vertical-align:middle;
}

.back-btn:hover {
  cursor: pointer;
}

.back-btn:hover .previous-btn {
  color: #bd537e;
}

.previous-btn-icon {
  margin-right: 10px;
  display:inline-block;
  vertical-align:middle;
  height: 20px;
}
</style>
