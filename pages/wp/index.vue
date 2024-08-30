<template>
  <div>
    <h1>ブログ記事一覧</h1>
    <ul>
      <li v-for="post in posts" :key="post.id">
        <h2>
          <nuxt-link :to="`/wp/posts/${post.id}`">{{
            post.title.rendered
          }}</nuxt-link>
        </h2>
        <div v-html="post.excerpt.rendered"></div>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { useFetch } from "nuxt/app";

const { data: posts, error } = await useFetch(
  "https://public-api.wordpress.com/wp/v2/sites/sgyamashita.wordpress.com/posts"
);

if (error.value) {
  console.error("Error fetching posts:", error.value);
}
</script>
