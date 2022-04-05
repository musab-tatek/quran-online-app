<template>
  <div class="favorite md:mt-10 mt-5">
    <h1 class="md:text-4xl text-3xl dark:text-gray-300">Favorite Surah</h1>
    <p
      v-if="$store.state.local_favorite_surah.length == 0"
      class="text-lg dark:text-gray-400"
    >
      No favorite Surah yet. Add it right away!
    </p>
    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6 mt-6" v-else>
      <Surah
        v-for="surah in $store.state.local_favorite_surah"
        :key="surah.number"
        :number="surah.number"
        :name="surah.name"
        :arabic_name="surah.arabic_name"
        :ayat="surah.ayat"
        :revelation="surah.revelation"
        :favorite="true"
      ></Surah>
    </div>
    <transition name="slide-fade">
      <success-modal v-if="$store.state.showModal"
        />
    </transition>
  </div>
</template>

<script>
export default {
  transition: 'fade',
};
</script>