<template>
    <v-app-bar app color="red" dark elevate-on-scroll>
        <v-toolbar-title class="title">LibreLol</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items>
            <v-btn text href="https://uptime.libre.lol/status/services" class="button">Uptime</v-btn>
            <v-btn text @click="showTOSDialog = true" class="button">Terms of Service</v-btn>
        </v-toolbar-items>

        <!-- Dialog for Terms of Service -->
        <v-dialog v-model="showTOSDialog" max-width="600px">
            <v-card>
                <v-card-title class="text-center">
                    <h2 class="headline">Terms of Service</h2>
                </v-card-title>
                <v-divider></v-divider>
                <v-card-text>
                    <p>Welcome to LibreLol! These terms and conditions outline the rules and regulations for the use of our website. By accessing or using LibreLol, you agree to comply with these terms. If you do not agree with any part of these terms, you must not use our services.</p>

                    <h3>1. Introduction</h3>
                    <p>By accessing this website, we assume you accept these terms and conditions. Do not continue to use LibreLol if you do not agree to all of the terms stated on this page.</p>

                    <h3>2. Cookies</h3>
                    <p>We employ the use of cookies. By accessing LibreLol, you consent to the use of cookies in accordance with our Privacy Policy. You can choose to accept or decline cookies.</p>

                    <h3>3. User Responsibilities</h3>
                    <p>Users are responsible for their conduct on the platform. You agree not to use LibreLol for any unlawful purpose, and you shall comply with all applicable laws and regulations.</p>

                    <h3>4. Government Cooperation</h3>
                    <p>LibreLol has not been contacted by any government entity for access to, modification of, or oversight of our services or data. We do not share user information with government agencies unless required by law.</p>

                    <h3>5. Disclaimer</h3>
                    <p>LibreLol hosts open-source software that anyone can use. We are not responsible for any actions committed by members. Users should exercise due diligence before using any of our services. We are not liable for any harm, damage, or misuse of services.</p>

                    <h3>6. Modifications</h3>
                    <p>We reserve the right to modify these terms at any time. Any changes will be posted on this page, and it is your responsibility to review these terms periodically. Continued use of the website after changes indicates your acceptance of the new terms.</p>

                    <h3>7. Contact Information</h3>
                    <p>If you have any questions about these Terms of Service, please contact us at <a href="mailto:support@librelol.com">support@librelol.com</a>.</p>
                </v-card-text>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="red" text @click="showTOSDialog = false">Close</v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </v-app-bar>
</template>

<script>
export default {
    name: 'TopBar',
    data() {
        return {
            showTOSDialog: false,
        };
    },
};
</script>

<style scoped>
.v-app-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
    border-bottom: 2px solid #ff3d00;
    padding: 0 16px; /* Add padding for better spacing */
}

.title {
    font-size: 1.8rem; /* Increased font size for better visibility */
    font-weight: bold;
    text-transform: uppercase; /* Uppercase for added emphasis */
}

.button {
    margin-left: 16px; /* Spacing between buttons */
}

.headline {
    font-size: 1.5rem; /* Adjusted size for dialog title */
    font-weight: 600; /* Slightly lighter weight for the title */
    color: red; /* Consistent color with the app bar */
}

.v-dialog .v-card {
    border-radius: 10px; /* Rounded corners for the dialog */
}

.v-card-text {
    line-height: 1.6; /* Improved line height for readability */
}

.v-card-actions {
    justify-content: flex-end; /* Align actions to the right */
}
</style>
