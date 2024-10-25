<template>
    <v-container fluid>
        <v-row class="mb-4">
            <v-col cols="12" class="d-flex justify-center">
                <v-text-field
                    v-model="searchQuery"
                    placeholder="Search..."
                    class="search-bar"
                    solo
                ></v-text-field>
            </v-col>
        </v-row>
        <v-row class="d-flex justify-center" :class="{ 'scrollable': filteredCategories.length >= 3 }">
            <v-col 
                v-for="(category, index) in filteredCategories" 
                :key="index" 
                cols="12" 
                md="4"
                class="d-flex justify-center"
            >
                <v-card elevation="2" class="formatted-card">
                    <v-card-title class="text-center font-weight-bold">
                        {{ category.title }}
                    </v-card-title>
                    <v-divider></v-divider>
                    <v-list dense>
                        <v-list-item
                            v-for="(link, idx) in category.links"
                            :key="idx"
                            :href="link.url"
                            target="_blank"
                            rel="noopener noreferrer"
                            class="link-item"
                        >
                            <v-list-item-icon>
                                <v-icon 
                                    v-if="link.iconType === 'mdi'" 
                                    :style="{ color: link.color || 'inherit' }"
                                >
                                    {{ link.icon }}
                                </v-icon>
                                <img 
                                    v-else 
                                    :src="link.icon" 
                                    alt="" 
                                    class="icon" 
                                    :style="{ filter: link.color ? `invert(${link.color})` : 'none' }" 
                                />
                            </v-list-item-icon>
                            <v-list-item-content>
                                <v-list-item-title class="font-weight-semibold">
                                    {{ link.name }}
                                </v-list-item-title>
                                <v-list-item-subtitle class="subtitle">
                                    {{ link.description }}
                                </v-list-item-subtitle>
                            </v-list-item-content>
                        </v-list-item>
                    </v-list>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import categories from '../categories.json'; // Adjust the path as necessary

export default {
    name: 'Links',
    data() {
        return {
            categories,
            searchQuery: '', // Added search query
        };
    },
    computed: {
        filteredCategories() {
            // Filter categories based on search query in titles, links, and descriptions
            return this.categories.map(category => ({
                ...category,
                links: category.links.filter(link =>
                    link.name.toLowerCase().includes(this.searchQuery.toLowerCase()) ||
                    link.description.toLowerCase().includes(this.searchQuery.toLowerCase())
                )
            })).filter(category => category.links.length > 0); // Only include categories with matching links
        },
    },
}
</script>

<style scoped>
.search-bar {
    max-width: 400px; /* Set a max width for the search bar */
    width: 100%; /* Full width */
    border-radius: 24px; /* Rounded corners */
}

.scrollable {
    overflow-x: auto; /* Enable horizontal scrolling */
    white-space: nowrap; /* Prevent wrapping of columns */
}

.formatted-card {
    border-radius: 12px;
    transition: transform 0.3s, box-shadow 0.3s;
    width: 400px; /* Standard width */
    margin: 16px; /* Spacing between cards */
}

.formatted-card:hover {
    transform: scale(1.05);
    box-shadow: 0 6px 30px rgba(0, 0, 0, 0.2);
}

.link-item {
    transition: background-color 0.2s;
}

.link-item:hover {
    background-color: rgba(255, 255, 255, 0.1);
}

.icon {
    width: 24px;
    height: 24px;
}

.subtitle {
    color: #757575;
}

.font-weight-semibold {
    font-weight: 600;
}

/* Media Queries */
@media (max-width: 768px) {
    .scrollable {
        overflow-x: hidden; /* Disable scrolling on mobile */
        display: flex; /* Allow cards to expand */
        flex-wrap: wrap; /* Wrap items */
    }
}
</style>
