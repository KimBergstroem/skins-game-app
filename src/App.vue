<template>
  <div class="container">
    <header>
      <h1>Simple Easy Skins</h1>
      <input v-model.trim="search" type="text" placeholder="Search..." />
      <button class="btn-steam">Sign In With Steam</button>
    </header>
    <div class="wrapper">
      <h1>Games</h1>
      <div class="options-container">
        <div v-for="quiz in quizes" :key="quiz.id" class="card">
          <img :src="quiz.img" :alt="quiz.name" />
          <div class="card-text">
            <h2>{{ quiz.name }}</h2>
            <p>
              <span>{{ quiz.questions.length }}</span> Online
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import q from "./data/quizes.json"; // Import of all the questions in the quiz json file
import { ref, watch } from "vue";

const quizes = ref(q); // Making state variable from the json file with the quizes
const search = ref(""); // Empty search state

// Everytime search state is changed, it triggers the filter and include function on the v-for attribute
// to display the cards that is in the serach input
watch(search, () => {
  quizes.value = q.filter((quiz) =>
    quiz.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>

<style scoped>
.container {
  max-width: 1000px;
  margin: 0 auto;
}

header {
  margin-bottom: 10px;
  margin-top: 30px;
  display: flex;
  align-items: center;
}

header h1 {
  font-weight: bold;
  margin-right: 30px;
  color: white;
}

header input {
  border: none;
  background-color: rgba(128, 128, 128, 0.1);
  padding: 10px;
  border-radius: 5px;
}

.options-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 15px;
}

.btn-steam {
  background-color: rgb(30, 47, 78);
  color: white;
  border: none;
  border-radius: 5px;
  margin-left: 20px;
  padding: 10px;
  font-weight: bold;
  cursor: pointer;
}

.wrapper {
  margin-top: 50px;
  color: white;
}
/* ------------------> CARD STYLE */
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
