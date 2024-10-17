<template>
  <div class="headerContainer">
    <header class="header">
      <div class="logo">
        <img src="assets/images/logo.png" width="150px" alt="Logo" />
      </div>
      <nav class="navigation">
        <ul>
          <li><NuxtLink to="/">الرئيسية</NuxtLink></li>
          <li><NuxtLink to="/about">نبذة عنا</NuxtLink></li>
          <li><NuxtLink to="/services">الخدمات</NuxtLink></li>
          <li><NuxtLink to="/contact">تواصل معنا</NuxtLink></li>
        </ul>
      </nav>
    </header>
  </div>
</template>

<script setup></script>

<style scoped>
.headerContainer {
  background-color: var(--card-color);
  color: white;
  padding: 10px 0px;
  width: 100%;
}

.header {
  display: flex;
  justify-content: space-between;
  
  align-items: center;
  width: 80%;
  margin: auto;
}

.navigation ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  display: flex;
}

.navigation li {
  margin-left: 20px;
}

.navigation a {
  color: var(--text-color);
  font-size: 25px;
  text-decoration: none;
}

.navigation a:hover {
  text-decoration: underline;
 
}
</style>
