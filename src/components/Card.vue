<template>
  <div class="card">
    <img :src="quiz.img" :alt="quiz.name" />
    <div class="card-text">
      <h2>{{ quiz.name }}</h2>
      <p>
        <span>{{ quiz.questions.length }}</span> Online
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref, defineProps } from "vue";

const { quiz } = defineProps(["quiz"]);
</script>

<style scoped>
.card {
  width: 310px;
  overflow: hidden;
  border-radius: 2%;
  box-shadow: 1px 1px 10px rgb(0, 0, 0, 0.1);
  margin-bottom: 35px;
  margin-right: 20px;
  cursor: pointer;
  background-color: rgb(30, 47, 78);
  color: white;
}

.card img {
  width: 100%;
  height: 190px;
  margin: 0;
}

.card .card-text {
  padding: 10px 10px;
}

.card .card-text h2 {
  font-weight: bold;
}

.card .card-text span {
  color: rgb(6, 255, 6);
  font-weight: bold;
}
</style>
