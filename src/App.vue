<script setup>
import { ref  } from "vue";
import startScreen from './components/startScreen.vue';
import { GoogleGenAI } from "@google/genai";

const question = ref( '' );

const startQuiz = async(topic) => {
  const ai = new GoogleGenAI({ apiKey: "AIzaSyCVBijHOwf5nnP3XV7iIa_2X-t5wK5VoyM" });

  const response = await ai.models.generateContent({
      model: "gemini-2.0-flash",
      contents: `Can you give me the latest news that impact trade for ${ topic }`,
    });
    question.value = response.text;
}
</script>

<template>
  <h1>Analisis de trading</h1>
  <div id="app">

    <header>
      <div class="container">

      </div>
    </header>

    <start-screen @start-quiz="startQuiz" />
    <p>
      {{ question }}
    </p>
  </div>
</template>
