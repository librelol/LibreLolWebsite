<template>
    <v-col cols="auto">
        <v-card elevation="1" class="pa-4">
            <v-card-title class="font-weight-bold text-center">
                Social Links
            </v-card-title>
            <v-divider></v-divider>
            <v-list dense>
                <v-list-item v-for="(link, index) in links" :key="index" :href="link.url" target="_blank" rel="noopener noreferrer">
                    <v-list-item-icon>
                        <img :src="link.icon" alt="" class="icon" />
                    </v-list-item-icon>
                    <v-list-item-content>
                        <v-list-item-title>{{ link.name }}</v-list-item-title>
                        <v-list-item-subtitle>{{ link.description }}</v-list-item-subtitle>
                    </v-list-item-content>
                </v-list-item>
            </v-list>
        </v-card>
    </v-col>
</template>

<script>
export default {
    name: 'Links',
    data() {
        return {
            links: [
                { 
                    name: 'Telegram', 
                    url: 'https://t.me/yourchannel', 
                    icon: 'https://cdn.simpleicons.org/telegram/0088cc', // Telegram blue
                    description: 'Join our Telegram channel' 
                },
                { 
                    name: 'X', 
                    url: 'https://x.com/librelol', 
                    icon: 'https://cdn.simpleicons.org/x/FFFFFF', // White color
                    description: 'Follow us on Twitter' 
                },
            ],
        };
    },
}
</script>

<style scoped>
.v-card {
    border-radius: 8px;
}

.v-list-item {
    transition: background-color 0.2s;
}

.v-list-item:hover {
    background-color: rgba(0, 0, 0, 0.05);
}

.icon {
    width: 20px;  /* Adjusted for size */
    height: 20px; /* Adjusted for size */
}
</style>
