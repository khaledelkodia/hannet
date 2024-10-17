<template>
  <div>
    <div class="flex justify-around mt-2 text-4xl">
      <p class="text-center w-20">{{ remainingTime.seconds }}</p>
      <p class="text-center w-20">{{ remainingTime.minutes }}</p>
      <p class="text-center w-20">{{ remainingTime.hours }}</p>
      <p class="text-center w-20">{{ remainingTime.days }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

// استلام التاريخ كـ prop
const props = defineProps({
  eventDate: Date,
});

const remainingTime = ref({
  days: 0,
  hours: 0,
  minutes: 0,
  seconds: 0,
});

// دالة لحساب الفرق بين التاريخ الحالي وتاريخ الحدث
const calculateTimeDifference = () => {
  const now = new Date();
  const timeDiff = props.eventDate - now; // الفارق بالمللي ثانية

  if (timeDiff > 0) {
    const totalSeconds = Math.floor(timeDiff / 1000);

    remainingTime.value.days = Math.floor(totalSeconds / (60 * 60 * 24));
    remainingTime.value.hours = Math.floor(
      (totalSeconds % (60 * 60 * 24)) / (60 * 60)
    );
    remainingTime.value.minutes = Math.floor((totalSeconds % (60 * 60)) / 60);
    remainingTime.value.seconds = Math.floor(totalSeconds % 60);
  } else {
    // في حال كان الوقت قد مر بالفعل
    remainingTime.value = { days: 0, hours: 0, minutes: 0, seconds: 0 };
  }
};

// تحديث العدّاد كل ثانية
let interval;
onMounted(() => {
  calculateTimeDifference(); // حساب الفارق فورًا عند التحميل
  interval = setInterval(calculateTimeDifference, 1000); // التحديث كل ثانية
});

onBeforeUnmount(() => {
  clearInterval(interval); // تنظيف الـ interval عند إزالة المكون
});
</script>
