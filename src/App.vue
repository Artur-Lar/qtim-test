<template>
  <div class="nav">
    <img src="@/assets/logo.svg" alt="logo" />
    <div class="nav_rightPart">
      <ul class="nav_list">
        <li><a class="nav_list_item" href="#">Works</a></li>
        <li><a class="nav_list_item" href="#">About</a></li>
      </ul>
      <img class="lang" src="@/assets/language.svg" alt="lang" />
      <button class="nav_btn">Let’s work</button>
    </div>
  </div>
  <router-view />
  <MainFooter />
</template>

<script>
import MainFooter from "@/components/MainFooter.vue";

export default {
  components: {
    MainFooter,
  },
};
</script>

<style>
body {
  margin: auto;
  box-sizing: border-box;
  font-family: "TT Commons", sans-serif;
  max-width: 1440px;
}
.nav {
  display: flex;
  justify-content: space-between;
  font-family: "TT Commons", sans-serif;
  width: 95%;
  height: 120px;
  align-items: center;
  margin: auto;
}
.nav_rightPart {
  display: flex;
}
.nav_list {
  list-style: none;
  display: flex;
  gap: 60px;
  padding-right: 90px;
}
.nav_list_item {
  text-decoration: none;
  color: inherit;
}
.lang {
  margin-right: 15px;
}
.nav_btn {
  font-family: "TT Commons", sans-serif;
  padding: 16px 32px;
  align-items: flex-start;
  gap: 10px;
  color: white;
  border-radius: 999px;
  background: var(--Style, #101010);
}
</style>
