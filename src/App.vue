<script setup>
/*
I tried to create a handy webapp to keep track of all the movies I've watched this year and which was my favorite, but form bindings are confusing and it's not working properly :(

Can you help me fix it?

level 1: Update the movie list with a v-for loop so all movies in the provided file movies.json are rendered. Feel free to update/change the list to your likes, or to add more info for each movie.

level 2: Create a small "movie card" for each movie object in the list and display in it the title, a small poster picture, and the score of the movie.

level 3: Remove the duplicated & hardcoded code in the form binding for "My fav movie" selector, and use a v-for loop and attribute bindings to correctly build the options. (Note: you can change the binding variable 'favoriteMovie' below if needed)

level 4: I want it to be easy to see which one is my current favorite, so please add a "😍" emoji next to the title to my favorite movie in the list.

level 5: The score of each film is represented by a string with a value between "0" and "100". We can do better! Let's show between 1 to 5 stars in each film card, according to the score (tip: use a v-for loop here).

level 6: Fix the multiselectors of the movies I've watched this year. Remove the duplicated & hardcoded code in the form binding for both multi selectors, and use v-for loops and attribute bindings to correctly build the options. Keep in mind they should be synchronized! (keep using the same binding to the variable "watchedList" for both fields).

level 7: The multiselectors are nice, but it would be great to also have a checkbox on each film card to mark it as watched/not watched. Of course, it should be synchronized with the "watchedList" array!

bonus level: Apply your CSS magic and designer's touch to make the app look great!
*/

import { ref } from 'vue';
import movies from './assets/movies.json';
import StarReating from './components/StarReating.vue';

const favoriteMovie = ref('');
const watchedList = ref([]);
</script>

<template>
  <h3>Her Is Movie list</h3>
  
    <ul>
      <div class="card" v-for="movie in movies" :key="movie.id">
        <img :src="movie.picture" /> <br />
        <div class="container">
        Title: {{ movie.title }}
        <h2 v-if="movie.title == favoriteMovie">😍</h2>

        <br />

        <StarReating :score="Number(movie.score)"></StarReating>
        <input
          type="checkbox"
          id="option1"
          :value="movie.title"
          v-model="watchedList"
        />
        <label for="option1">Movie that is watched</label>
        Score: {{ movie.score }}
      </div>
        </div>

    </ul>


  <hr />
  <h3>Controls</h3>
  <div>
    <span>My fav movie: {{ favoriteMovie || 'none chosen yet :(' }}</span>
    <br />
    <br />
    <select v-model="favoriteMovie">
      <option v-for="movie in movies" :key="movie.id" :value="movie.title">
        {{ movie.title }}
      </option>
    </select>
  </div>

  <hr />

  <div>
    <span>Movies watched this year: {{ watchedList }}</span>
    <br />
    <br />
    <select v-model="watchedList" multiple>
      <option v-for="movie in movies" :key="movie.id" :value="movie.title">
        {{ movie.title }}
      </option>
    </select>
  </div>

  <hr />
  <div>
    <span>Movies watched this year: {{ watchedList }}</span>
    <br />
    <br />
    <div v-for="movie in movies" :key="movie.id" :value="movie.title">
      <input type="checkbox" :value="movie.title" v-model="watchedList" />
      <label for="option1">{{ movie.title }}</label>
      <br />
    </div>
  </div>
</template>


