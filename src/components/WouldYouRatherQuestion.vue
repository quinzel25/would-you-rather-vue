<template>

<!--template for the html -->
    <div class="question-container">
<!--        a list element that will be re-used for each item in the questions object array-->
        <ul id="question-list">
<!--            v-for does the work for us-->
            <li v-for="q in questions" :key="q.question" id="line">
                <h2>{{q.question}}</h2>
<!--                q.id makes sure that we can only select one radio button per question-->
                <input  type="radio"  v-bind:value="q.answer1" v-model="q.id" v-on:change="$emit('answer-change', q.id)">
                <label id="label1">{{q.answer1}}</label>
                <input  type="radio"  v-bind:value="q.answer2"  v-model="q.id" v-on:change="$emit('answer-change', q.id)">
                <label id="label2">{{q.answer2}}</label>
            </li>

        </ul>

    </div>



</template>
<!--script-->
<script>
    export default {
        name: "WouldYouRatherQuestion",
        data() {
            // array of our data
            return {
                questions: [
                    {id: 0,
                    question: '...be the author of a popular book or a musician in a band who released a popular album?',
                    answer1: 'be an author of a popular book',
                    answer2: 'be a musician with a popular album'
                    },
                    {id: 1,
                        question: '...live in a place with a lot of trees or live in a place near the ocean?',
                        answer1: 'live by a lot of trees',
                        answer2: 'live by the ocean'
                    },
                    {id: 2,
                        question: '...eat a whole raw onion or a whole lemon?',
                        answer1: 'eat a whole raw onion',
                        answer2: 'eat a whole lemon'
                    }

                ],



            }
        },

    }
</script>

<style>
#line {
    margin: 20px;
    border: 10px;
    background-color: #f8dc88;


}
   #label1,#label2 {
       font-size: 16px;

   }
</style>