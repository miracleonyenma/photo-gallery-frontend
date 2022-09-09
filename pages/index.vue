<script setup>
const { data } = await useFetch("/api/getAllPhotos")
</script>
<template>
  <main class="site-main photos-page">
    <div class="wrapper">
      <section class="gallery-section">
        <div class="wrapper">
          <header>
            <h1 class="text-xl">All photos</h1>
          </header>

          <ul v-if="data && data?.listPhotos?.data" class="gallery">
            <li
              v-for="(photo, i) in data.listPhotos.data"
              :key="i"
              class="group gallery-item"
            >
              <div class="photo img-cont">
                <img :src="photo.photo" alt="image" />
                <div class="backdrop group-hover:opacity-100"></div>
              </div>
              <div class="details">
                <div class="author-details group-hover:opacity-100">
                  <h3 class=" text-lg"> {{photo.author.name}} </h3>
                  <p> @{{ photo.author.username }} </p>
                </div>
                <p class="caption">
                  {{ photo.caption }}
                </p>
              </div>
            </li>
          </ul>
          <div v-else class="gallery-error">
            <p>Oops.. No photos to display</p>
          </div>
        </div>
      </section>
    </div>
  </main>
</template>
