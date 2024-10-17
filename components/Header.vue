<template>
  <div class="headerContainer">
    <header class="header">
      <div class="logo">
        <img src="assets/images/logo.png" width="150px" alt="Logo" />
      </div>

      <!-- زر فتح القائمة الجانبية في الشاشات الصغيرة -->
      <button class="menu-btn" @click="isSidebarOpen = true">☰</button>

      <!-- القائمة الجانبية -->
      <aside :class="['sidebar', { open: isSidebarOpen }]">
        <button class="close-btn" @click="isSidebarOpen = false">X</button>
        <ul>
          <li><NuxtLink to="/" @click="isSidebarOpen = false">الرئيسية</NuxtLink></li>
          <li><NuxtLink to="/about" @click="isSidebarOpen = false">نبذة عنا</NuxtLink></li>
          <li><NuxtLink to="/" @click="isSidebarOpen = false">الخدمات</NuxtLink></li>
          <li><NuxtLink to="/" @click="isSidebarOpen = false">تواصل معنا</NuxtLink></li>
        </ul>
      </aside>

      <!-- القائمة العادية للشاشات الكبيرة -->
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

<script setup>
import { ref } from 'vue';
const isSidebarOpen = ref(false);
</script>

<style scoped>
.headerContainer {
  background-color: var(--card-color);
  color: white;
  padding: 10px 0px;
  width: 100%;
  height: 102px;
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

.menu-btn {
  background: none;
  border: none;
  color: white;
  font-size: 30px;
  cursor: pointer;
  display: none;
}

/* القائمة الجانبية */
.sidebar {
  position: fixed;
  top: 0px;
  right: -300px;
  width: 300px;
  height: 100%;
  background-color: var(--card-color);
  box-shadow: -2px 0 5px rgba(0, 0, 0, 0.5);
  padding: 20px;
  transition: right 0.7s ease-out;
  z-index: 1000;
}

.sidebar.open {
  right: 0;
}

.sidebar ul {
  list-style-type: none;
  padding: 0;
}

.sidebar li {
  margin-bottom: 20px;
}

.sidebar a {
  color: white;
  font-size: 20px;
  text-decoration: none;
  direction: rtl
}

.close-btn {
  background: none;
  border: none;
  color: white;
  font-size: 25px;
  cursor: pointer;
  display: block;
  margin-left: auto;
}

/* إخفاء القائمة العادية في الشاشات الصغيرة */
@media (max-width: 900px) {
  .navigation {
    display: none;
  }
  
  .menu-btn {
    display: block;
  }
}
</style>
