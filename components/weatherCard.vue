<template>
  <div class="weatherContainer mb-8" v-for="city in displayedCities" :key="city.id">
    <div class="weatherInfo">
      <img
        class="image z-10"
        :src="`/images/weather/${city.weather[0].icon}.png`"
        alt="Weather Icon"
      />
      <div class="relative">
        <h1 class="text-9xl ">{{ Math.round(city.main.temp - 273.15) }}</h1>
        <p class="text-xl top-1 -right-2 absolute">°C</p>
        <h1 class="absolute -bottom-2 left-5">{{ city.name }}</h1>
      </div>
      <h1 class="absolute text-lg bottom-3 right-10">{{ getDay() }}</h1>
      
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

// تعريف المتغيرات
const cities = ref([]);
const displayedCities = ref([]);

// دالة الفيتش للحصول على بيانات الطقس
const fetchWeatherData = async () => {
  try {
    const apiKey = "d6e9ac8e785193a3114bca3cc97b652d"; // ضع هنا مفتاح الـ API الخاص بك
    const cityIds = "360630,108410,292223,285787"; // قائمة الـ IDs للمدن المطلوبة
    const url = `https://api.openweathermap.org/data/2.5/group?id=${cityIds}&appid=${apiKey}`;

    const response = await fetch(url);
    const data = await response.json();
    cities.value = data.list; // البيانات الخاصة بالمدن
    displayedCities.value = cities.value; // عرض المدن في واجهة المستخدم
  } catch (error) {
    console.error("Error fetching weather data:", error);
  }
};

// استدعاء الفيتش عند تحميل الصفحة
onMounted(() => {
  fetchWeatherData();
});

// دالة لجلب اليوم الحالي
const getDay = () => {
  const days = [
    "الأحد",
    "الاثنين",
    "الثلاثاء",
    "الأربعاء",
    "الخميس",
    "الجمعة",
    "السبت",
  ];
  const today = new Date();
  return days[today.getDay()];
};
</script>

<style scoped>
.weatherContainer {
  width: 250px;
  height: 220px;
  background-color: var(--card-color);
  border-radius: 12px;
  padding: 5px;
  text-align: center;
  position: relative;
  display: flex;
  flex-direction: column; /* لترتيب العناصر بشكل عمودي */
  justify-content: center;
  align-items: center;
}

.weatherContainer img {
  position: absolute;
  bottom: -40px;
  left: -65px;
  width: 170px;
}




.city-name {
  padding-left: 60px;
}

/*------------ شاشة 1815 ------------*/
@media (max-width: 1815px) {
  .weatherContainer {
    width: 250px;
  }

  .title {
    font-size: 50px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}

/*------------ شاشة 1544 ------------*/
@media (max-width: 1544px) {
  .weatherContainer {
    width: 280px;
  }

  .title {
    font-size: 40px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}
/*------------ شاشة 1366 ------------*/
@media (max-width: 1366px) {
  .weatherContainer {
    width: 260px;
  }

  .title {
    font-size: 40px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}

/*------------ شاشة 1347 ------------*/
@media (max-width: 1347px) {
  .weatherContainer {
    width: 230px;
  }

  .title {
    font-size: 40px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}

/*--------------- شاشة 1024 ---------------*/
@media (max-width: 1024px) {
  .weatherContainer {
    width: 250px;
  }

  .title {
    font-size: 40px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}

/*--------------- شاشة 955 ---------------*/
@media (max-width: 955px) {
  .weatherContainer {
    width: 230px;
  }
  .title {
    font-size: 60px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}

/*--------------- شاشة 600 ---------------*/
@media (max-width: 600px) {
  .weatherContainer {
    width: 230px;
  }

  .title {
    font-size: 40px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .weatherContainer img {
  position: absolute;
  bottom: -40px;
  left: -40px;
  width: 140px;
}
}
/*--------------- شاشة 560 ---------------*/
@media (max-width: 560px) {
  .weatherContainer {
    width: 240px;
  }

  .title {
    font-size: 40px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .weatherContainer img {
  position: absolute;
  bottom: -30px;
  left: -25px;
  width: 120px;
}
}

/*--------------- شاشة 538 ---------------*/
@media (max-width: 538px) {
  .weatherContainer {
    width: 280px;
  }

  .title {
    font-size: 40px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .weatherContainer img {
  position: absolute;
  bottom: -60px;
  left: -60px;
  width: 180px;
}
}
/*--------------- شاشة 400 ---------------*/
@media (max-width: 400px) {
  .weatherContainer {
    width: 280px;
  }
  .title {
    font-size: 35px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}
</style>
