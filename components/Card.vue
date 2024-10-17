<template>
  <div class="card">
    <div class="layersCard">
      <img
        class="image mx-auto object-cover"
        :src="imageUrl"
        alt="Event Image"
      />
      <div class="text-group">
        <div class="titleUp">{{ titleUp }}</div>
        <div class="title">{{ title }}</div>
        <div class="titleDown">{{ titleDown }}</div>
      </div>
    </div>
    <div class="flex justify-around mt-4 text-xl">
      <p class="text-center w-20">ثانية</p>
      <p class="text-center w-20">دقيقة</p>
      <p class="text-center w-20">ساعة</p>
      <p class="text-center w-20">يوم</p>
    </div>
    <!-- <div class=" flex justify-around mt-2 text-4xl ">
      <p class="text-center w-20">59</p>
      <p class="text-center w-20">59</p>
      <p class="text-center w-20">23</p>
      <p class="text-center w-20">360</p>

    </div> -->
    <CountDown :eventDate="eventDate" />
  </div>
</template>

<script setup>
// استلام الحقول من الـ props
const props = defineProps({
  title: String,
  titleUp: String,
  titleDown: String,
  eventDate: Date,
  imageUrl: String,
});

import CountDown from "./CountDown.vue";
</script>

<style scoped>
.card {
  background-color: var(--card-color);
  width: 500px;
  height: 351px;
  border-radius: 12px;
  padding: 5px;
  text-align: center;
}

.layersCard {
  position: relative;
}
.image {
  width: 95%;
  height: 225px;
  border-radius: 12px;
  margin-top: 10px;
  opacity: calc(30%);
}

.text-group {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  flex-direction: column;
  align-items: center;
}

.titleUp {
  align-self: flex-end;
  font-size: 20px;
}

.title {
  font-size: 60px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.titleDown {
  align-self: flex-start;
  margin-top: 10px;
  font-size: 20px;
}

/*------------ شاشة 1815 ------------*/
@media (max-width: 1815px) {
  .card {
    width: 450px;
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
  .card {
    width: 380px;
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
  .card {
    width: 391px;
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
  .card {
    width: 350px;
  }

  .title {
    font-size: 40px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}

/*------------ شاشة 1212 ------------*/
@media (max-width: 1212px) {
  .card {
    width: 320px;
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
  .card {
    width: 420px;
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
  .card {
    width: 530px;
  }
  .title {
    font-size: 60px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}

/*--------------- شاشة 640 ---------------*/
@media (max-width: 640px) {
  .card {
    width: 400px;
  }

  .title {
    font-size: 40px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}

/*--------------- شاشة 400 ---------------*/
@media (max-width: 400px) {
  .title {
    font-size: 35px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
}
</style>
