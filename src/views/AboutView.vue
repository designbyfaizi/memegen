<template>
  <div class="about">
    <button @click="getMemes">Get Memes</button>
    <p class="anime">Anime: {{meme.anime}}</p>
    <p class="anime">Character: {{meme.character}}</p>
    <p class="anime">Quote: {{meme.quote}}</p>
    <!-- <p>{{ meme }}</p> -->
  </div>
</template>

<script setup lang="ts">
import axios from "axios";
import { ref } from "vue";

let meme = ref({});

var options = {
  method: "GET",
  url: "https://animechan.vercel.app/api/random",
};

function getMemes() {
  axios
    .request(options)
    .then((response) => {
      meme.value = response.data;
      console.log(response.data)
    })
    .catch((err) => {
      console.log(err);
    });
}
</script>

<!-- <script lang="ts">
import axios from "axios";
export default {
  data() {
    return {
      meme: {},
    };
  },
  methods: {
    getMemes() {
      var options = {
        method: "GET",
        url: "https://animechan.vercel.app/api/random",
      };
      axios
        .request(options)
        .then((response) => {
          this.meme = response.data;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script> -->

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
}

.anime {
  background: black;
  padding: 1rem 2rem;
  margin: 1rem;
}
</style>
