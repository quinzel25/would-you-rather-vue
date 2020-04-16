<template>
  <!--  main template for the page-->
  <div id="app">
        <div style="background-color: #f76a8c" class="jumbotron">
            <h1>Would you rather...</h1>
        </div>

        <!--    this adds the template from the vue component-->
<!--        this grabs the $emit data from child component and calls the method we are using-->
        <would-you-rather-question
        v-on:answer-change="answerChange"></would-you-rather-question>
<!--      the results part of the page-->
      <div id="results">
            <h2>You would rather...</h2>
          <ul id="result-list">

<!--                v-show so that if it's true it will display list items-->
              <li v-show="answerOne">{{answerOne }} <br></li>
              <li v-show="answerTwo">{{answerTwo}} <br></li>
              <li v-show="answerThree">{{answerThree}}</li>
          </ul>

      </div>

  </div>
</template>




<script>


  import WouldYouRatherQuestion from "../../would-you-rather-vue/src/components/WouldYouRatherQuestion";

  export default {
    name: 'App',
    data() {
      return {
          // these are the variables that display our result set
          answerOne: '',
          answerTwo: '',
          answerThree: '',
      }
    },
    components: {
      //grab this from import
      WouldYouRatherQuestion
    },
    methods: {
        // method here
        // 'choice' is the data the child emitted to parent
        answerChange(choice) {
            // Probably not the best way to do this part but hey it works ¯\_(ツ)_/¯

            //first question
            let testString1 = 'be an author of a popular book'
            let testString2 = 'be a musician with a popular album'
            if (choice === testString1 || choice === testString2) {
                this.answerOne = choice

            }
            // second question
            let testString3 = 'live by a lot of trees'
            let testString4 = 'live by the ocean'

            if (choice === testString3 || choice === testString4) {
                this.answerTwo = choice

            }
            // third question
            let testString5 = 'eat a whole raw onion'
            let testString6 = 'eat a whole lemon'

            if (choice === testString5 || choice === testString6) {
                this.answerThree = choice

            }
        }

    }
  }


</script>

<style>
    #app {
        margin: 40px 0 0;
        text-align: center;

    }
    ul {
        list-style-type: none;
        padding: 0;
    }
    li {
        display: inline-block;
        margin: 0 10px;
    }
    body {
        background-color: #c6ead9;
    }

    /*.jumbotron {*/
    /*    background-color: #215c41;*/
    /*    text-emphasis-color: #42b983;*/
    /*}*/

</style>
