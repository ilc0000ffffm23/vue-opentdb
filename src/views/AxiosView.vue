<template>

    <v-container fluid>
        <v-card color="teal lighten-1">
            <v-card-title>Axios Demonstration</v-card-title>
            <v-container>
            <v-btn @click="getQuestions">Generate OpenTDB</v-btn>
            <br>
            <br>
            <v-divider></v-divider>
            <br>
            <v-list-item v-for="question in questions" :key="questions.id">
                <v-list-item-title>{{unescapeHtml (question.question) }}</v-list-item-title>
                <v-list-item>
                    {{ question.correct_answer }}
                </v-list-item>
            </v-list-item>
            </v-container>
        </v-card>
    </v-container>

</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'

const questions = ref([])

async function getQuestions() {
    axios.get('https://opentdb.com/api.php?amount=10&category=18&difficulty=easy&type=multiple').then(response => {
        questions.value = (response.data.results)

    })   
}

function unescapeHtml(str){
    return str
    .replace(/&amp;/g, "&")
    .replace(/&lt;/g, "<")
    .replace(/&gt;/g, ">")
    .replace(/&quot;/g, "\"")
    .replace(/&#039;/g, "\'");
}
</script>

<style>

</style>