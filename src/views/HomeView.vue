<template>
  <div class="articles_container">
    <div class="articles">Articles</div>
    <SingleArticle />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import SingleArticle from "@/components/SingleArticle.vue"; // @ is an alias to /src
import MainFooter from "@/components/MainFooter.vue";

@Options({
  components: {
    SingleArticle,
    MainFooter,
  },
})
export default class HomeView extends Vue {}
</script>

<style>
.articles_container {
  width: 85%;
  margin: auto;
  padding-top: 120px;
}
.articles {
  font-family: TT Commons;
  font-size: 84px;
}
</style>
