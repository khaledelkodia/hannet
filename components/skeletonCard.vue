<template>
  <div class="skeletonCard">
    <svg class="w-72 m-auto" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200">
      <circle
        fill="none"
        stroke-opacity="1"
        stroke="#FFFFFF"
        stroke-width=".5"
        cx="100"
        cy="100"
        r="0"
      >
        <animate
          attributeName="r"
          calcMode="spline"
          dur="2"
          values="1;80"
          keyTimes="0;1"
          keySplines="0 .2 .5 1"
          repeatCount="indefinite"
        ></animate>
        <animate
          attributeName="stroke-width"
          calcMode="spline"
          dur="2"
          values="0;25"
          keyTimes="0;1"
          keySplines="0 .2 .5 1"
          repeatCount="indefinite"
        ></animate>
        <animate
          attributeName="stroke-opacity"
          calcMode="spline"
          dur="2"
          values="1;0"
          keyTimes="0;1"
          keySplines="0 .2 .5 1"
          repeatCount="indefinite"
        ></animate>
      </circle>
    </svg>
  </div>
</template>

<script setup></script>

<style scoped>
.skeletonCard {
  background-color: var(--card-color);
  width: 500px;
  height: 351px;
  border-radius: 12px;
  padding: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
}


/*------------ شاشة 1815 ------------*/
@media (max-width: 1815px) {
  .skeletonCard {
    width: 450px;
  }
}

/*------------ شاشة 1544 ------------*/
@media (max-width: 1544px) {
  .skeletonCard {
    width: 380px;
  }
}

/*------------ شاشة 1366 ------------*/
@media (max-width: 1366px) {
  .skeletonCard {
    width: 391px;
  }
}

/*------------ شاشة 1347 ------------*/
@media (max-width: 1347px) {
  .skeletonCard {
    width: 350px;
  }
}

/*------------ شاشة 1212 ------------*/
@media (max-width: 1212px) {
  .card {
    width: 320px;
  }
}

/*--------------- شاشة 1024 ---------------*/
@media (max-width: 1024px) {
  .skeletonCard {
    width: 420px;
  }
}

/*--------------- شاشة 955 ---------------*/
@media (max-width: 955px) {
  .skeletonCard {
    width: 530px;
  }
}

/*--------------- شاشة 640 ---------------*/
@media (max-width: 640px) {
  .skeletonCard {
    width: 400px;
  }
}
</style>
