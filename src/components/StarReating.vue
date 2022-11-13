<script setup>
import { ref } from 'vue';
const props = defineProps({ score: Number });
const MARKER = '⭐';

const normalizedScore = ref(Math.ceil(props.score / 20));
</script>

<template>
  <div>
    <span v-for="i in normalizedScore">{{ MARKER }}</span>
  </div>
  <div>
    <span v-if="score >= 90">
      {{ MARKER }}{{ MARKER }}{{ MARKER }}{{ MARKER }}{{ MARKER }}
    </span>
    <span v-else-if="score >= 80">
      {{ MARKER }} {{ MARKER }} {{ MARKER }} {{ MARKER }}
    </span>
    <span v-else-if="score >= 60">
      {{ MARKER }} {{ MARKER }} {{ MARKER }}
    </span>
    <span v-else-if="score >= 40"> {{ MARKER }} {{ MARKER }} </span>
    <span v-else> {{ MARKER }}</span>
  </div>
</template>
