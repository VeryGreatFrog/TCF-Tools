<template>
    <div class="map-selector">
        <div class="map-buttons">
            <div class="button-content" :class="selectedMap.get() == 1 ? 'selected-map' : 'not-selected-map'" @click="selectedMap.set(1)" role="button">
                <p>Map 1</p>
                <p>Bright Sands</p>
            </div>
            <div class="button-content" :class="selectedMap.get() == 2 ? 'selected-map' : 'not-selected-map'" @click="selectedMap.set(2)" role="button">
                <p>Map 2</p>
                <p>Crescent Falls</p>
            </div>
            <div class="button-content" :class="selectedMap.get() == 3 ? 'selected-map' : 'not-selected-map'" @click="selectedMap.set(3)" role="button">
                <p>Map 3</p>
                <p>Tharis Island</p>
            </div>
        </div>
    </div>
</template>
<script lang="ts">
import {defineComponent} from 'vue';
import {selectedMap} from '../store';
export default defineComponent({
    data() {
        return {
            selectedMap,
        };
    },
});
</script>
<style scoped>
.map-selector {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
}
.map-buttons {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    gap: 1.25rem;
}

.button-content {
    background-color: var(--color-surface-4);
    width: 33%;
    display: flex;
    justify-content: space-between;
    cursor: pointer;
    padding: 1rem;
    border: 1px solid var(--border-color-base);
    transition: all 0.2s ease-in-out;
}

.button-content:hover {
    color: var(--link-footer-color);
}
.selected-map {
    border-color: var(--rarity-color-uncommon);
}
.not-selected-map {
    border-color: var(--rarity-color-exotic);
}
.selected-map::after {
    content: '✔';
    color: var(--rarity-color-uncommon);
}
.not-selected-map::after {
    content: '✖';
    color: var(--rarity-color-exotic);
}

.disabled {
    border-color: var(--rarity-color-common);
    text-decoration: line-through;
}

@media screen and (max-width: 900px) {
    .map-buttons {
        flex-direction: row;
    }
}
</style>
