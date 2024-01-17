<template>
  <div class="footer">
    <div class="footer-container">
      <div class="footer-up">
        <div class="footer-left-side">
          <p>Is there a project?</p>
          <div class="lets-work">
            <span class="underline-text">Let’s work</span>
            <span class="underline-text">together</span>
          </div>
        </div>
        <div class="footer-rigth-side">
          <p>For all questions</p>

          <p>+7 (920) 278—00—68 qtim@agency.com</p>
          <p>Office in Russia</p>
          <p>139 Ruben Station Lake Drew, NM 52678</p>
          <img src="@/assets/button location.png" alt="location-button" />
          <p>Office in Dubai</p>
          <p>139 Ruben Station Lake Drew, NM 52678</p>
          <img src="@/assets/button location.png" alt="location-button" />
        </div>
      </div>
      <div class="footer-dowm">
        <a href="#">Facebook</a>
        <a href="#">Instagram</a>
        <a href="#">Telegram</a>
        <div class="semi-circle">Go</div>
        <a href="#">Behance</a>
        <a href="#">Linkedn</a>
        <a href="#">Privacy Policy</a>
      </div>
    </div>
  </div>
</template>

<script></script>

<style>
.footer {
  background: var(--Style, #e2beff);
}
.footer-container {
  width: 85%;
  margin: auto;
}
.footer-up {
  display: flex;
  padding-top: 140px;
}
.footer-rigth-side {
  width: 160px;
  padding-top: 70px;
}
.footer-left-side {
  width: 460px;
  padding-right: 20%;
}
.footer p {
  font-size: 16px;
}
.lets-work {
  font-size: 112px;
  display: inline-block;
}
.underline-text {
  position: relative;
}

.underline-text::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: 6px;
  width: 100%;
  height: 1px;
  background-color: #808080; /* Серый цвет подчеркивания */
}
.footer-dowm {
  display: flex;
  align-items: end;
  justify-content: space-between;
  padding-top: 140px;
}
.footer-dowm a {
  padding-bottom: 30px;
  color: black;
}
.semi-circle {
  width: 360px;
  height: 180px;
  background-color: black;
  color: white;
  border-radius: 180px 180px 0 0;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-left: 10%;
  margin-right: 10%;
}
</style>
