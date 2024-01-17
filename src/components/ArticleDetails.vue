<template>
  <div class="article-detail">
    <div class="title">{{ article.title }}</div>
    <img :src="article.image" :alt="article.title" />
    <div class="about">About</div>
    <p>{{ article.description }}</p>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      article: {
        title: "",
        image: "",
        description: "",
      },
    };
  },
  watch: {
    "$route.params.id": "fetchArticleDetails",
  },
  mounted() {
    const articleId = this.$route.params.id;
    this.fetchArticleDetails(articleId);
  },
  methods: {
    async fetchArticleDetails(articleId) {
      try {
        const response = await fetch(
          `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/${articleId}`
        );
        const data = await response.json();
        this.article = data;
      } catch (error) {
        console.error("Error fetching article details:", error);
      }
    },
  },
};
</script>

<style scoped>
.article-detail {
  width: 85%;
  margin: auto;
}
.about {
  padding-top: 80px;
}
.title {
  font-size: 84px;
  padding-top: 120px;
  padding-bottom: 80px;
}
.article-detail img {
  width: 100%;
}
.article-detail p {
  width: 700px;
  font-size: 36px;
}
</style>
