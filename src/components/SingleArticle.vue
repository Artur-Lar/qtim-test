<template>
  <div>
    <div class="container">
      <div v-for="article in articles" :key="article.id" class="single_article">
        <router-link
          class="router-link"
          :to="{ name: 'ArticleDetails', params: { id: article.id } }"
        >
          <img :src="article.image" :alt="article.title" />
          <div class="article-preview">{{ article.preview }}</div>
        </router-link>
      </div>
    </div>

    <div class="pagination">
      <button @click="changePage(1)" :disabled="currentPage === 1">1</button>
      <button
        v-for="pageNumber in [2, 3, 4, 5, 'next']"
        :key="pageNumber"
        @click="handlePaginationClick(pageNumber)"
        :class="{ active: currentPage === pageNumber && pageNumber !== 'next' }"
      >
        {{ pageNumber === "next" ? "&gt;" : pageNumber }}
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  data() {
    return {
      articles: [] as Array<{
        id: string;
        image: string;
        title: string;
        preview: string;
      }>,
      currentPage: 1,
      pageSize: 8,
      totalArticles: 0,
    };
  },
  computed: {
    totalPages(): number {
      return Math.ceil(this.totalArticles / this.pageSize);
    },
  },
  mounted() {
    this.fetchArticles();
  },
  methods: {
    async changePage(pageNumber: number) {
      this.currentPage = pageNumber;
      await this.fetchArticles();
    },
    async fetchArticles() {
      try {
        const response = await fetch(
          `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts?page=${this.currentPage}&limit=${this.pageSize}`
        );
        const data = await response.json();
        this.articles = data as Array<{
          id: string;
          image: string;
          title: string;
          preview: string;
        }>;

        // Обновляем общее количество статей с сервера
        this.totalArticles = parseInt(
          response.headers.get("X-Total-Count") || "0",
          10
        );
      } catch (error) {
        console.error("Error fetching data:", error);
      }
    },
    handlePaginationClick(pageNumber: number | string) {
      if (pageNumber === "next" && this.currentPage < this.totalPages) {
        this.changePage(this.currentPage + 1);
      } else {
        this.changePage(
          pageNumber === "next" ? this.currentPage + 1 : (pageNumber as number)
        );
      }
    },
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  grid-gap: 30px;
  justify-content: space-around;
}
.router-link {
  text-decoration: none;
}
.router-link img {
  width: 260px;
}
.article-preview {
  font-family: "TT Commons", sans-serif;
  font-size: 20px;

  color: black;
}
.pagination {
  margin-top: 50px;
  margin-bottom: 140px;
}

.pagination button {
  margin-right: 8px;
  width: 44px;
  height: 44px;
  padding: 11px 17px;
  border: none;
  border-radius: 12px;
}

.pagination button.active {
  background-color: black;
  color: #fff;
}
</style>
