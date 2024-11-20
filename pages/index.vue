<template>
  <div v-if="loading" class="cardContainer">
    <SkeletonCard />
    <SkeletonCard />
    <SkeletonCard />
  </div>

  <div v-if="!loading" class="cardContainer">
    <Card
      v-for="(item, index) in items"
      :key="index"
      :title="item.title"
      :titleUp="item.titleUp"
      :titleDown="item.titleDown"
      :eventDate="new Date(item.date)"
      :imageUrl="item.imageUrl"
    />
  </div>
  <div>
    <Website />
  </div>
  <div class=" text-center text-3xl my-8 ">الطقس</div>
  <div class="weatherCardContainer">
    <WeatherCard />
  </div>
  <div class=" text-center text-3xl my-8 ">إعرف مرتبك </div>
  <div>
    <IncomeCalculation />
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";


const items = ref([]);
const loading = ref(true); // متغير حالة التحميل

onMounted(async () => {
  try {
    const response = await fetch("https://dummyjson.com/c/2aed-63cd-45e7-a95e");
    const data = await response.json();

    // وضع البيانات المستلمة في المتغير
    items.value = data.map((item) => ({
      title: item.title,
      titleUp: item.titleUp,
      titleDown: item.titleDown,
      date: item.date,
      imageUrl: item.imageUrl,
    }));

    // تغيير حالة التحميل إلى false لما البيانات توصل
    loading.value = false;
  } catch (error) {
    console.error("Error fetching data:", error);
    loading.value = false; // في حالة الخطأ برضه وقف التحميل
  }
});
</script>

<style scoped>
.cardContainer {
  margin-top: 20px;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 20px;
  
}

.weatherCardContainer {
  margin-top: 20px;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 48px;
  
}

@media (max-width: 1024px) {
  .cardContainer > Card {
    flex: 1 1 calc((100% - 20px) / 2);
    max-width: none;
  }
}

@media (max-width: 768px) {
  .cardContainer > Card {
    flex: 1 1 100%;
    max-width: none;
  }
}
</style>
