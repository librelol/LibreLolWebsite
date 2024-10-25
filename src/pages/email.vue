<template>
    <v-container class="pa-5">
        <v-row>
            <v-col cols="12" md="8" offset-md="2">
                <v-card elevation="2" class="pa-4">
                    <v-card-title class="font-weight-bold text-center">
                        Contact Information
                    </v-card-title>
                    <v-divider></v-divider>
                    <v-card-text>
                        <div class="text-center">
                            <p>
                                <strong>Email:</strong> <a :href="`mailto:${email}`">{{ email }}</a>
                            </p>
                            <p>
                                <strong>PGP Key:</strong>
                            </p>
                            <pre class="pgp-key">{{ pgpKey }}</pre>
                        </div>
                    </v-card-text>
                    <v-card-actions>
                        <v-spacer></v-spacer>
                        <v-btn color="blue" @click="downloadPGPKey">
                            Download PGP Key
                        </v-btn>
                    </v-card-actions>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
export default {
    name: 'ContactInfo',
    data() {
        return {
            email: 'hello@libre.lol', // Replace with your email
            pgpKey: `-----BEGIN PGP PUBLIC KEY BLOCK-----

xjMEZkwJDRYJKwYBBAHaRw8BAQdAomxExkuSFeiWKv5b2X3uIJ/yiVsB2W/M
KSaQUIEdPC3NIWhlbGxvQGxpYnJlLmxvbCA8aGVsbG9AbGlicmUubG9sPsKM
BBAWCgA+BYJmTAkNBAsJBwgJkME+T67QbMb/AxUICgQWAAIBAhkBApsDAh4B
FiEEzn/MX3p3XhiMCLPzwT5PrtBsxv8AAELuAQDdlRc8AQ2uSp0Ed8eYl4S2
wBg2GamZJaY7GtGb61iNtQD+Lzf50rpf21xb4vEn2L6PT04y8dixNIaLguPR
xMQARwrOOARmTAkNEgorBgEEAZdVAQUBAQdAoy9vvyNfdHfOK95II5Hk+tEh
rGc5Q+zwO//cCnzVlTkDAQgHwngEGBYKACoFgmZMCQ0JkME+T67QbMb/ApsM
FiEEzn/MX3p3XhiMCLPzwT5PrtBsxv8AAM0MAPsFYYAN1XFFaiZ9dwLGjvvM
cvtORVVOSesvc1plzoSqKQD9FlKOMu3IunxKIBuHmwVGy21m2JbGWCvz48rH
aqALYAs=
=Hy5s
-----END PGP PUBLIC KEY BLOCK-----
`,
        };
    },
    methods: {
        downloadPGPKey() {
            const blob = new Blob([this.pgpKey], { type: 'text/plain' });
            const link = document.createElement('a');
            link.href = window.URL.createObjectURL(blob);
            link.download = 'librelol.asc';
            link.click();
        },
    },
};
</script>

<style scoped>
.pgp-key {
    border: 1px solid #ccc;
    padding: 10px;
    border-radius: 4px;
    white-space: pre-wrap; /* Keeps formatting of the PGP key */
    overflow: auto; /* Allows scrolling if necessary */
}
</style>
