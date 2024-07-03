<script setup>
import { ref, watch } from 'vue';
import QuizCard from './components/QuizCard.vue';
import srcQuiz from './data/quizes.json';

const quizes = ref(srcQuiz);
const search = ref('');

watch(search, () => {
  quizes.value = srcQuiz.filter((quiz) =>
    quiz.title.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>

<template>
  <main class="max-width-[900px] mx-auto px-8">
    <header class="flex items-center gap-8 mt-8">
      <h1 class="text-3xl font-bold">QuizVue</h1>
      <input
        v-model.trim="search"
        type="text"
        placeholder="search..."
        class="p-2 rounded-md bg-slate-200 focus:outline-blue-400"
      />
    </header>

    <section class="py-10 xl:py-16">
      <div class="flex flex-wrap gap-7">
        <QuizCard v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
        <!-- <div
          class="card width-[270px] rounded-2xl overflow-hidden shadow-md"
          v-for="quiz in quizes"
          :key="quiz.id"
        >
          <img
            :src="quiz.img"
            :alt="quiz.title"
            class="w-full h-[180px] object-cover"
          />
          <div class="p-4 card-body">
            <a class="font-bold cursor-pointer hover:underline">{{
              quiz.title
            }}</a>
            <p class="mt-2 text-sm">{{ quiz.questions.length }}</p>
          </div>
        </div> -->
      </div>
    </section>
  </main>
</template>
