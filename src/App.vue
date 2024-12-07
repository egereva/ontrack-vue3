<template>
    <TheHeader @go-to-timiline="goTo(PAGE_TIMELINE)" @go-to-progress="goTo(PAGE_PROGRESS)" />

    <main class="flex flex-grow flex-col">
        <TheTimeline v-show="currentPage === PAGE_TIMELINE" />
        <TheActivities v-show="currentPage === PAGE_ACTIVITIES" />
        <TheProgerss v-show="currentPage === PAGE_PROGRESS" />
    </main>

    <TheNav :current-page="currentPage" @navigate="goTo($event)" />
</template>

<script setup>
import { ref } from 'vue'
import TheHeader from './components/TheHeader.vue'
import TheNav from './components/TheNav.vue'
import { PAGE_ACTIVITIES, PAGE_PROGRESS, PAGE_TIMELINE } from './constants'
import TheActivities from './pages/TheActivities.vue'
import TheProgerss from './pages/TheProgerss.vue'
import TheTimeline from './pages/TheTimeline.vue'
import { normalizePageHash } from './functions'

const currentPage = ref(normalizePageHash())

function goTo(page) {
    currentPage.value = page
}
</script>
