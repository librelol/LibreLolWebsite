<template>
    <v-container>
        <v-row>
            <v-col 
                v-for="(category, index) in categories" 
                :key="index" 
                cols="12" 
                md="4"
            >
                <v-card elevation="2" class="pa-4 mb-4 card-animated">
                    <v-card-title class="font-weight-bold text-center">
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
                            class="list-item-animated"
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
                                <v-list-item-title class="font-weight-semibold">{{ link.name }}</v-list-item-title>
                                <v-list-item-subtitle class="subtitle">{{ link.description }}</v-list-item-subtitle>
                            </v-list-item-content>
                        </v-list-item>
                    </v-list>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
export default {
    name: 'Links',
    data() {
        return {
            categories: [
                {
                    title: 'Social Links',
                    links: [
                        { 
                            name: 'Telegram', 
                            url: 'https://t.me/yourchannel', 
                            icon: 'https://cdn.simpleicons.org/telegram/0088cc', 
                            iconType: 'simple',
                            color: '#0088cc', 
                            description: 'Join our Telegram channel for updates and discussions.' 
                        },
                        { 
                            name: 'X', 
                            url: 'https://x.com/librelol', 
                            icon: 'https://cdn.simpleicons.org/x/FFFFFF', 
                            iconType: 'simple',
                            color: '#FFFFFF', 
                            description: 'Follow us on X for news and announcements.' 
                        },
                    ],
                },
                {
                    title: 'Proxies',
                    links: [
                        { 
                            name: 'Searx', 
                            url: 'https://search.libre.lol', 
                            icon: 'https://cdn.simpleicons.org/searxng/0088cc', 
                            iconType: 'simple',
                            color: '#0088cc', 
                            description: 'Search the web privately with Searx.' 
                        },
                        { 
                            name: 'Invidious', 
                            url: 'https://inv.libre.lol', 
                            icon: 'mdi-play-box',
                            iconType: 'mdi',
                            color: '#FF0000', 
                            description: 'Watch YouTube videos securely without ads.' 
                        },
                        {
                            name: 'Wikiless',
                            url: 'https://wikiless.libre.lol',
                            icon: 'mdi-wikipedia',
                            iconType: 'mdi',
                            color: '#000000',
                            description: 'Access Wikipedia articles without tracking.'
                        }
                    ],
                },
                {
                    title: 'Recommended Services',
                    links: [
                        { 
                            name: 'Mullvad VPN', 
                            url: 'https://mullvad.net', 
                            icon: 'mdi-vpn', 
                            iconType: 'mdi',
                            color: '#008000', 
                            description: 'A trusted VPN provider known for privacy and security.' 
                        },
                        { 
                            name: 'Proton Mail', 
                            url: 'https://proton.me/mail', 
                            icon: 'https://cdn.simpleicons.org/protonmail/8B89CC', 
                            iconType: 'simple',
                            color: '#8B89CC', 
                            description: 'Secure and encrypted email for privacy-conscious users.' 
                        },
                        {
                            name: 'Telegraph',
                            url: 'https://telegra.ph',
                            icon: 'mdi-newspaper',
                            iconType: 'mdi',
                            color: '#0088cc',
                            description: 'Publish articles and stories anonymously.'
                        }
                    ],
                },
                {
                    title: 'Tools',
                    links: [
                        { 
                            name: 'Private Bin', 
                            url: 'https://paste.libre.lol', 
                            icon: 'mdi-file-document', 
                            iconType: 'mdi',
                            color: '#000000', 
                            description: 'An open-source paste bin alternative focused on privacy.' 
                        },
                        { 
                            name: 'Git', 
                            url: 'https://git.libre.lol', 
                            icon: 'mdi-git', 
                            iconType: 'mdi',
                            color: '#F05032', 
                            description: 'A self-hosted Git service for the public.' 
                        },
                        { 
                            name: 'Vaultwarden', 
                            url: 'https://pass.libre.lol', 
                            icon: 'mdi-lock', 
                            iconType: 'mdi',
                            color: '#FFD700', 
                            description: 'Manage your passwords securely with this Bitwarden alternative.' 
                        },
                    ],
                },
                {
                    title: "Notable Mentions",
                    links: [
                        {
                            name: 'UNSPA',
                            url: 'https://unspa.com',
                            icon: 'mdi-school',
                            iconType: 'mdi',
                            color: '#FF0000',
                            description: 'American Nationalist Group'
                        }
                    ],
                }
            ],
        };
    },
}
</script>

<style scoped>
.v-card {
    border-radius: 12px;
    transition: transform 0.3s, box-shadow 0.3s;
}

.v-card:hover {
    transform: scale(1.05);
    box-shadow: 0 6px 30px rgba(0, 0, 0, 0.2);
}

.v-list-item {
    transition: background-color 0.2s;
}

.v-list-item:hover {
    background-color: rgba(255, 255, 255, 0.1);
}

.list-item-animated {
    transition: transform 0.2s;
}

.list-item-animated:hover {
    transform: translateX(5px);
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
</style>
