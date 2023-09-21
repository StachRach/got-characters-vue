<template>
  <footer>
    <div class="footer">
      <a href=https://github.com/StachRach/got-characters-vue.git target="_blank">
        <button>Go to GitHub</button>
      </a>
      <p><span>Stanisław Rachwał &emsp;</span>| &emsp; Made in 2023</p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  width: 100%;
  background-color: black;
  color: white;
  text-align: center;
  text-transform: uppercase;
  padding: 20px 0 2px 0;
}

.footer span {
  color: red;
}

.footer button {
  color: black;
  border: 2px solid #36013f;
  padding: 20px;
  transition: 0.4s;
  font-size: 14px;
}

.footer button:hover {
  background-color: #36013f;
  color: white;
  cursor: pointer;
}
</style>