<template>
    <div class="mt-7">
        <ul>
            <TimelineItem
                v-for="timelineItem in timelineItems"
                :key="timelineItem.hour"
                :timelineItem="timelineItem"
            />
        </ul>
    </div>
</template>

<script setup>
import TimelineItem from '../components/TimelineItem.vue'
import { generateTimelineItems } from '../functions'

const timelineItems = generateTimelineItems()
</script>

<style lang="scss" scoped></style>
