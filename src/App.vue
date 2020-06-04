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
              <div class="answer" @click="setQuestionnaireStep(index)"><span class="index-bold">{{index+1}}.</span> {{answer}}</div>
          </div>
        </div>
      </div>

      <div v-if="questionnaireStep === 1">
        <h2>{{step1.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step1.answers" :key="index">
            <div class="answer" @click="setQuestionnaireStep(index)"><span class="index-bold">{{index+1}}.</span> {{answer}}</div>
          </div>
        </div>
      </div>

      <div v-if="questionnaireStep === 1.1">
        <h2>{{step1_1.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step1_1.answers" :key="index">
            <div class="answer" @click="setQuestionnaireStep(index)"><span class="index-bold">{{index+1}}.</span> {{answer}}</div>
          </div>
        </div>  
      </div>

      <div v-if="questionnaireStep === 1.2">
        <h2>{{step1_2.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step1_2.answers" :key="index">
            <div class="answer" @click="setQuestionnaireStep(index)"><span class="index-bold">{{index+1}}.</span> {{answer}}</div>
          </div>
        </div>  
      </div>

      <div v-if="questionnaireStep === 2">
        <h2>{{step2.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step2.answers" :key="index">
            <div class="answer" @click="setQuestionnaireStep(index)"><span class="index-bold">{{index+1}}.</span> {{answer}}</div>
          </div>
        </div>
      </div>

      <div v-if="questionnaireStep === 3">
        <h2>{{step3.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step3.answers" :key="index">
            <div class="answer" @click="setQuestionnaireStep(index)"><span class="index-bold">{{index+1}}.</span> {{answer}}</div>
          </div>
        </div>
      </div>

      <div v-if="questionnaireStep === 3.1">
        <h2>{{step3_1.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step3_1.answers" :key="index">
            <div class="answer" @click="setQuestionnaireStep(index)"><span class="index-bold">{{index+1}}.</span> {{answer}}</div>
          </div>
        </div>
      </div>

      <div v-if="questionnaireStep === 3.2">
        <h2>{{step3_2.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step3_2.answers" :key="index">
            <div class="answer" @click="setQuestionnaireStep(index)"><span class="index-bold">{{index+1}}.</span> {{answer}}</div>
          </div>
        </div>
      </div>
      <div v-if="questionnaireStep === 4">
        <h2>{{step4.question}}</h2>
        <div class="answer-container">
          <div v-for="(answer, index) in step4.answers" :key="index">
            <div class="answer" @click="setQuestionnaireStep(index)"><span class="index-bold">{{index+1}}.</span> {{answer}}</div>
          </div>
        </div>  
      </div>
      <div v-if="questionnaireStep === 5">
        <div class="final-answer-container">
          <div>Congratulations!</div>
          <br>
          <div><span class="description">{{"You succesfully completed the project. When the project is done, users are no longer a part of the design process. However, it is important that the internal team evaluates all methodologies which were used during the design process. It is recommended to list the pros, cons, the problems they faced, and most importantly, what could be improved. This will allow them to use participatory design methodologies in a better and more efficient way next time. User interviews can be conducted to help with the evaluation."}}</span></div>
        </div>
      </div>
    </div>

    <div v-if="finalAnswer || finalAnswerDesc" class="final-answer-container">
      <div>You should use <span class="methodology">{{finalAnswer}}</span></div>
      <br>
      <div v-if="finalAnswerDesc"><span class="description">{{finalAnswerDesc}}</span></div>
    </div>

    <!-- <div class="finalAnswer" v-if="finalAnswer">You should use <span class="methodology">{{finalAnswer}}</span></div>
    <div v-if="finalAnswerDesc">{{finalAnswerDesc}}</div> -->

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
      finalAnswerDesc: "",
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
      step1: { // Project Initiation // SPREMEMBA
        question: "Do you already have a general idea about how your product will be designed?",
        answers: [
          "No",
          "Yes"
        ]
      },
      step1_1: { // Project Initiation NO // SPREMEMBA
        question: "You want to:",
        answers: [
          "Identify consumer problems.",
          "Find the right solution to a consumer problem.",
          "Clarify your idea and learn about your target audience. "
        ]
      },
      step1_2: { // Project Initiation YES // SPREMEMBA
        question: "You want to:",
        answers: [
          "Find some inovative ideas which will bring additional value to the project.",
          "Better define the interaction between a user and your product.",
          "Raise capital or outsource part of your work."
        ]
      },

      step2: { // Project Planing
        question: "You need to:",
        answers: [
          "Come up with additional ideas for setting goals.",
          "Prioritize ideas in order to determine a course of action.",
          "Solve a user related problem."
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
          "A cheap way to get a great insight into user’s minds.",
          "To definine and solve problems, come up with fresh ideas.",
          "To find the best (holistic) solution.",
          "Determine parts of the product and it’s functionalities.",
          "Help with designing the structure of a website or an application.",
          "To solve a user related problem."
        ]
      },
      step3_2: { // Project Execution NO
        question: "You want to:",
        answers: [
          "Definine and solve problems, come up with fresh ideas.",
          "See how users interact with the prototype.",
          "Use a cheap way to get a great insight into user’s minds.",
          "solve a user related problem"
        ]
      },
      step4: { // Project Monitoring
        question: "You need to:",
        answers: [
          "Solve problems and improve the execution process.",
          "Prioritize ideas or help determine a course of action."
        ]
      },
      step5: { // Project Closing
        question: "Congratulations",
        answers: [
          "You're done"
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
        case 1.1:
          this.setQuestionnaireStepFrom1_1(answerId);
          break;
        case 1.2:
          this.setQuestionnaireStepFrom1_2(answerId);
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
          this.setQuestionnaireStepFrom4(answerId);
          break;
        case 5:
          this.setQuestionnaireStepFrom5(answerId);
          //this.finalAnswer = "No participatory design methodologies can be used in this project phase";
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
        case 4:
          this.previousStep = this.questionnaireStep;
          this.questionnaireStep = 5;
          break;
        case 5:
          this.previousStep = this.questionnaireStep;
          this.questionnaireStep = 6;
          break;
        
      }
    },
    setQuestionnaireStepFrom1(answerId) { // Project Initiation
      switch (answerId) {
        case 0:
          this.previousStep = this.questionnaireStep;
          this.questionnaireStep = 1.1;
          break;
        case 1:
          this.previousStep = this.questionnaireStep;
          this.questionnaireStep = 1.2;
          break;
      }
    },
    setQuestionnaireStepFrom1_1(answerId) { // Project Initiation NO
      switch (answerId) {
        case 0:
          this.finalAnswer = "User stories";
          this.finalAnswerDesc = "User stories can be used to identify consumer problems. Organizations can then decide to design a product or service around that problem. If an organization wants its users to choose their product over their competitor’s it needs to add value to consumer’s life by fulfilling their needs or satisfying their desires.";
          break;
        case 1:
          this.finalAnswer = "World cafe";
          this.finalAnswerDesc = "Cafe style of conversations turned out to be a great way to openly discuss ideas and solve problems. It has a unique power to link ideas within a larger group to access the collective intelligence of the participants. By using this method we can easily access innovation and action that are already present in any group. It may not be the most effective way to solve problems but it is a great way to explore different perspectives of an idea and come up with some innovative thoughts which can later be applied in the design process. ";
          break;
        case 2:
          this.finalAnswer = "Storyboarding";
          this.finalAnswerDesc = "This methodology can be used by individuals or groups. It requires a pen and some paper and no drawing skills. Storyboarding will help individuals to think their ideas through. Storyboards can also be acted out in front of the whole team to get feedback or find investors. ";
          break;
      }
    },
    setQuestionnaireStepFrom1_2(answerId) { // Project Initiation YES
      switch (answerId) {
        case 0:
          this.finalAnswer = "Brainstorming";
          this.finalAnswerDesc = "Brainstorming is appropriate for both small and large organizations of all kinds. It encourages creative thinking and can also be used for solving problems. The suggestions that come up during the session can be very inspiring. Organizations can use them to come up with interesting and unusual ideas or create a better solution to a problem. Brainstorming can be practiced individually or in groups. In both cases, the participants are encouraged to share their opinions freely. During the stage of generating ideas, criticism is not allowed. Even the craziest ideas are welcomed and built upon.";
          break;
        case 1:
          this.finalAnswer = "User stories";
          this.finalAnswerDesc = "User stories can be used to describe the interaction between the user and a system. They break down those interactions into individual tasks which help organizations to understand the user’s goals and motivations. Here is an example of a user story representing an iCloud subscriber: 'As an iCloud subscriber, I want a reliable cloud service so I can access my files at any time.'";
          break;
        case 2:
          this.finalAnswer = "Crowdsourcing";
          this.finalAnswerDesc = "Crowdsourcing is being used across various industries, for various reasons. There are many benefits a crowd can contribute to an organization such as funding, problem-solving, market research, innovative ideas, etc.";
          break;
      }
    },
    setQuestionnaireStepFrom2(answerId) { // Project Planning
      switch (answerId) {
        case 0:
          this.finalAnswer = "Brainstorming";
          this.finalAnswerDesc = "Brainstorming is appropriate for both small and large organizations of all kinds. It encourages creative thinking and can also be used for solving problems. The suggestions that come up during the session can be very inspiring. Organizations can use them to come up with interesting and unusual ideas or create a better solution to a problem. Brainstorming can be practiced individually or in groups. In both cases, the participants are encouraged to share their opinions freely. During the stage of generating ideas, criticism is not allowed. Even the craziest ideas are welcomed and built upon.";
          break;
        case 1:
          this.finalAnswer = "Crowd voting";
          this.finalAnswerDesc = "The crowd votes to determine the best. Organizations may use crowd voting to engage stakeholders, such as employees or customers, as well as the public to help prioritize ideas or help determine a course of action.";
          break;
        case 2:
          this.finalAnswer = "Five whys";
          this.finalAnswerDesc = "First you need to define a problem that needs solving. Design a broad question related to this problem. When the user answers the question, you should repeatedly ask the question “Why” to their response until they get to the root of the problem.";
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
          this.finalAnswer = "User interview";
          this.finalAnswerDesc = "Almost all user-related topics can be covered with this method, including the user experience understanding, usability of the product, the user’s motivations, and drawbacks. Interviewers can gain some fresh ideas which can be used to improve the product. All that needs to be done is finding the participants and conducting a good interview. If there’s a lack of resources or time, interviews can be done over the phone or an online conference call. However, the best way to practice this method is in person.";
          break;
        case 1:
          this.finalAnswer = "Brainstorming";
          this.finalAnswerDesc = "Brainstorming is appropriate for both small and large organizations of all kinds. It encourages creative thinking and can also be used for solving problems. The suggestions that come up during the session can be very inspiring. Organizations can use them to come up with interesting and unusual ideas or create a better solution to a problem. Brainstorming can be practiced individually or in groups. In both cases, the participants are encouraged to share their opinions freely. During the stage of generating ideas, criticism is not allowed. Even the craziest ideas are welcomed and built upon.";
          break;
        case 2:
          this.finalAnswer = "Crowd contest";
          this.finalAnswerDesc = "You may organize a crowd contest to broaden your horizons. The organizations may seek multiple qualified designers who will each submit their best ideas in the hopes of being the one winner who will be paid for producing the top design.";
          break;
        case 3:
          this.finalAnswer = "Collage";
          this.finalAnswerDesc = "This methodology is best used in the stage when we’re analyzing the context in which our product will be used. It can also be used to determine visual parts of the product (e.g. colors) and it’s functionalities. Collages can be done by individuals or groups. The participants can be given a specific number of pictures and words printed out in advance. They can also be totally free by choosing words and any kind of pictures, either from the internet or magazines. When they’re done, participants should explain the collage they made. This discussion will unlock new perspectives which may give the product some added value.";
          break;
        case 4:
          this.finalAnswer = "Card sort";
          this.finalAnswerDesc = "Card Sorting is a quick and easy way for organizations to spark the conversation about what matters most to the people they’re designing for. The design team can create a custom deck of cards. Each card can have some words written on it. Pictures can be used as well. To practice this methodology, the moderator puts a deck of cards in the user's hands and asks them to rank them in order of preference. Card sort methodology can also be used to start a deeper conversation about what users value and why.";
          break;
        case 5:
          this.finalAnswer = "Five whys";
          this.finalAnswerDesc = "First you need to define a problem that needs solving. Design a broad question related to this problem. When the user answers the question, you should repeatedly ask the question “Why” to their response until they get to the root of the problem.";
          break;
      }
    },
    setQuestionnaireStepFrom3_2(answerId) { // Project Execution v1
      switch (answerId) {
        case 0:
          this.finalAnswer = "Brainstorming";
          this.finalAnswerDesc = "Brainstorming is appropriate for both small and large organizations of all kinds. It encourages creative thinking and can also be used for solving problems. The suggestions that come up during the session can be very inspiring. Organizations can use them to come up with interesting and unusual ideas or create a better solution to a problem. Brainstorming can be practiced individually or in groups. In both cases, the participants are encouraged to share their opinions freely. During the stage of generating ideas, criticism is not allowed. Even the craziest ideas are welcomed and built upon.";
          break;
        case 1:
          this.finalAnswer = "Behavioral mapping";
          this.finalAnswerDesc = "This methodology can be used in different cases. Observing the users is always beneficial for the design process. By handing the product to the potential user and observing how they reenact with it, the design team can spot the imperfections which can make a huge difference to the user experience design. We can also find patterns of behaviors that help to determine what works and what doesn’t. This method is also used in parks, hospitals, shopping malls, and other public spaces in order to improve their functionality. ";
          break;
        case 2:
          this.finalAnswer = "User interview";
          this.finalAnswerDesc = "Almost all user-related topics can be covered with this method, including the user experience understanding, usability of the product, the user’s motivations, and drawbacks. Interviewers can gain some fresh ideas which can be used to improve the product. All that needs to be done is finding the participants and conducting a good interview. If there’s a lack of resources or time, interviews can be done over the phone or an online conference call. However, the best way to practice this method is in person.";
          break;
        case 3:
          this.finalAnswer = "Five whys";
          this.finalAnswerDesc = "First you need to define a problem that needs solving. Design a broad question related to this problem. When the user answers the question, you should repeatedly ask the question “Why” to their response until they get to the root of the problem.";
          break;
      }
    },
    setQuestionnaireStepFrom4(answerId) { // Project Monitoring
      switch (answerId) {
        case 0:
          this.finalAnswer = "Brainstorming";
          this.finalAnswerDesc = "Brainstorming is appropriate for both small and large organizations of all kinds. It encourages creative thinking and can also be used for solving problems. The suggestions that come up during the session can be very inspiring. Organizations can use them to come up with interesting and unusual ideas or create a better solution to a problem. Brainstorming can be practiced individually or in groups. In both cases, the participants are encouraged to share their opinions freely. During the stage of generating ideas, criticism is not allowed. Even the craziest ideas are welcomed and built upon.";
          break;
        case 1:
          this.finalAnswer = "Crowd voting";
          this.finalAnswerDesc = "The crowd votes to determine the best. Organizations may use crowd voting to engage stakeholders, such as employees or customers, as well as the public to help prioritize ideas or help determine a course of action.";
          break;
      }
    },
    goStepBack() {
      this.questionnaireStep = this.previousStep;
      this.finalAnswer = null;
      this.finalAnswerDesc = null;
      if(this.previousStep === 3) {
        this.previousStep = 0;
      }
      if(this.previousStep === 1) {
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
  /* text-align: left;

  float: left;
  position: relative;
  left: -50%; */
  padding: 0px 12px;
}

.answer:hover {
  color: #bd537e;
}

.answer-container {
  /* float: left;
  position: relative;
  left: 50%; */
  margin-bottom: 40px;
}

/* .finalAnswer {
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
} */

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

.final-answer-container {
  background-color: #333745;
  color: #D5CCCC;
  text-align: center;
  min-width: calc(100vw - 60px);
  border-radius: 20px;
  padding: 40px 4px;
  font-size: 24px;
  font-weight: 600;
  margin-top: 40px;
  position: relative;
}

.index-bold {
  font-weight: 600;
}

.description {
font-size: 17px;
font-weight: 100;
}
</style>
