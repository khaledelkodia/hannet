<template>
  <div class="headerContainer">
    <header class="header">
      <div class="logo">
        <img src="assets/images/logo.png" width="150px" alt="Logo" />
      </div>

      <!-- القائمة العادية للشاشات الكبيرة -->
      <nav class="navigation">
        <ul>
          <li><NuxtLink to="/">الرئيسية</NuxtLink></li>
          <li><NuxtLink to="/about">نبذة عنا</NuxtLink></li>
          <li><NuxtLink to="/">الخدمات</NuxtLink></li>
          <li><NuxtLink to="/">تواصل معنا</NuxtLink></li>
        </ul>
      </nav>

      <!-- زر فتح القائمة الجانبية في الشاشات الصغيرة -->
      <button class="menu-btn" @click.stop="toggleSidebar">☰</button>

      <!-- القائمة الجانبية للشاشات الصغيرة -->
      <aside
        ref="sidebar"
        class="sidebar"
        :class="{ open: isSidebarOpen }"
        @touchstart="startTouch"
        @touchend="endTouch"
      >
        <button class="close-btn" @click="toggleSidebar">X</button>
        <ul>
          <li><NuxtLink to="/" @click="toggleSidebar">الرئيسية</NuxtLink></li>
          <li>
            <NuxtLink to="/about" @click="toggleSidebar">نبذة عنا</NuxtLink>
          </li>
          <li><NuxtLink to="/" @click="toggleSidebar">الخدمات</NuxtLink></li>
          <li><NuxtLink to="/" @click="toggleSidebar">تواصل معنا</NuxtLink></li>
        </ul>
      </aside>
    </header>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const isSidebarOpen = ref(false); // حالة فتح/إغلاق السايدبار
let touchStartX = 0; // نقطة البداية للسحب
const sidebar = ref(null); // للإشارة إلى السايدبار

// دالة لتبديل حالة السايدبار بين الفتح والإغلاق
const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value;
};

// دالة لإغلاق السايدبار لما تضغط خارجها
const closeSidebar = (event) => {
  // التحقق إذا كان الكليك خارج السايدبار
  if (isSidebarOpen.value && !sidebar.value.contains(event.target)) {
    isSidebarOpen.value = false;
  }
};

// بداية السحب
const startTouch = (event) => {
  touchStartX = event.touches[0].clientX; // حفظ مكان اللمس الأول
};

// نهاية السحب
const endTouch = (event) => {
  const touchEndX = event.changedTouches[0].clientX; // حفظ مكان اللمس عند النهاية

  // إذا كان السحب لليمين (الفرق بين بداية ونهاية السحب موجب)
  if (touchEndX - touchStartX > 50) {
    // أكثر من 50px لضمان إنه سحب
    isSidebarOpen.value = false;
  }
};

// رصد الكليك في أي مكان في الصفحة
onMounted(() => {
  document.addEventListener("click", closeSidebar);
});

onUnmounted(() => {
  document.removeEventListener("click", closeSidebar);
});
</script>

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

.menu-btn {
  background: none;
  border: none;
  color: white;
  font-size: 30px;
  cursor: pointer;
  display: none; /* الزر ده مخفي في الشاشات الكبيرة */
}

.sidebar {
  position: fixed;
  top: 0;
  right: -300px;
  width: 300px;
  height: 100%;
  background-color: var(--card-color);
  box-shadow: -2px 0 5px rgba(0, 0, 0, 0.5);
  padding: 20px;
  transition: right 0.3s ease;
  direction: rtl;
  display: none; /* السايدبار مخفي في الشاشات الكبيرة */
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
}

.close-btn {
  background: none;
  border: none;
  color: white;
  font-size: 25px;
  cursor: pointer;
  display: block;
  margin-left: auto;
  border: 2px solid;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  margin-bottom: 20px;
  text-align: center;
}

/* للشاشات الصغيرة فقط */
@media (max-width: 900px) {
  .navigation {
    display: none; /* إخفاء القائمة العادية */
  }

  .menu-btn {
    display: block; /* إظهار زر القائمة الجانبية */
  }

  .sidebar {
    display: block; /* إظهار السايدبار */
  }
}
</style>
