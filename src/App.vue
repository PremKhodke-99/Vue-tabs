<template>
    <div class="homepage">
        <!-- Tabs -->
        <div class="tabs">
            <button v-for="tab in tabs" :key="tab.id" @click="selectedTab = tab.name"
                :class="{ active: selectedTab === tab.name }">
                {{ tab.label }}
            </button>
        </div>

        <!-- Cards -->
        <div class="cards">
            <div v-for="card in filteredCards" :key="card.id" class="card">
                <h3>{{ card.title }}</h3>
                <p>{{ card.description }}</p>
            </div>
        </div>
    </div>
</template>

<script>
import cardsData from "@/cards.json"; // Adjust path as necessary

export default {
    data() {
        return {
            tabs: [
                { id: 1, name: "tab1", label: "Tab 1" },
                { id: 2, name: "tab2", label: "Tab 2" }
            ],
            selectedTab: "tab1", // Default selected tab
            cards: {} // Store JSON data here
        };
    },
    computed: {
        filteredCards() {
            return this.cards[this.selectedTab] || [];
        }
    },
    mounted() {
        // Simulating fetching data
        this.cards = cardsData;
    }
};
</script>

<style>
/* Basic styling */
.tabs button {
    padding: 10px;
    margin: 5px;
    cursor: pointer;
}

.tabs .active {
    background-color: #007bff;
    color: white;
}

.cards .card {
    border: 1px solid #ddd;
    padding: 10px;
    margin: 10px;
}
</style>