<template>
  <div>
    <h1>{{ post.title.rendered }}</h1>
    <div v-html="post.content.rendered"></div>
  </div>
</template>

<script setup>
import { useFetch } from "nuxt/app";
import { useRoute } from "vue-router";

const route = useRoute();
const postId = route.params.id;

const { data: post, error } = await useFetch(
  `https://public-api.wordpress.com/wp/v2/sites/sgyamashita.wordpress.com/posts/${postId}`
);

if (error.value) {
  console.error("Error fetching post:", error.value);
}
</script>
