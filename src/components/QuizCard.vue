<script setup>
const { quiz } = defineProps(['quiz']);
</script>

<template>
  <div class="card width-[270px] rounded-2xl overflow-hidden shadow-md">
    <img
      :src="quiz.img"
      :alt="quiz.title"
      class="w-full h-[180px] object-cover"
    />
    <div class="p-4 card-body">
      <a class="font-bold cursor-pointer hover:underline">{{ quiz.title }}</a>
      <p class="mt-2 text-sm">{{ quiz.questions.length }} Questions</p>
    </div>
  </div>
</template>
