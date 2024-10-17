<template>
  <div class="containerWebsite w-[80%] mx-auto mt-8">
    <h1 class="text-center text-3xl">أهم المواقع</h1>
    <div class="website">
      <div v-for="(site, index) in sites" :key="index">
        <a :href="site.url" target="_blank">
          <img :src="site.image" :alt="site.title" />
          <p>{{ site.title }}</p>
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
const sites = ref([
  {
    image: "/images/websites/google.png",
    url: "https://www.google.com",
    title: "Google",
  },
  {
    image: "/images/websites/instagram.png",
    url: "https://www.instagram.com",
    title: "instagram",
  },
  {
    image: "/images/websites/facebook.png",
    url: "https://www.facebook.com",
    title: "Facebook",
  },
  {
    image: "/images/websites/whatsapp.png",
    url: "https://www.whatsapp.com",
    title: "Whatsapp",
  },
  {
    image: "/images/websites/twitterx.png",
    url: "https://www.x.com",
    title: "X",
  },
  {
    image: "/images/websites/tiktok.png",
    url: "https://www.tiktok.com",
    title: "Tiktok",
  },
]);
</script>

<style scoped>
.website {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  gap: 20px;
  margin-top: 2rem;
}
.website img {
  width: 100px;
  text-align: center;
}

.website p {
  text-align: center;
  font-size: 16px;
}

@media (max-width: 1024px) {
  .website img {
    width: 40px;
    text-align: center;
  }
  .website p {
    text-align: center;
    font-size: 8px;
  }
}
</style>
