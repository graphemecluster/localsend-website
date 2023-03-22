<template>
  <v-container class="fill-height">
    <v-row>

      <!-- Logo and text -->
      <v-col cols="12" sm="12" md="8" lg="6" xl="6" class="d-flex align-center">
        <v-row align="center">
          <v-col cols="12" md="4" class="d-flex justify-center justify-md-end">
            <img
              height="200"
              src="@/assets/logo-512.png"
            />
          </v-col>
          <v-col cols="12" md="auto">
            <h1 class="text-h2 text-xl-h1 font-weight-bold text-center text-md-start">LocalSend</h1>
            <h2 class="text-h5 text-xl-h4 text-center text-md-start">Share files to nearby devices.</h2>
            <div class="text-center text-md-start">
              <v-btn variant="tonal" size="x-large" class="mt-4" color="primary" :prepend-icon="mdiDownload" to="/download">
                Download
              </v-btn>
              <v-btn variant="tonal" size="x-large" class="ml-4 mt-4" :prepend-icon="mdiGithub" href="https://github.com/localsend/localsend" target="_blank">
                Github
              </v-btn>
            </div>
          </v-col>
        </v-row>
      </v-col>

      <!-- Screenshots -->
      <v-col cols="12" sm="12" md="4" lg="6" xl="6" class="pt-12 pt-md-0">
        <v-row class="d-none d-xl-flex">
          <v-col cols="12" md="6">
            <v-img
              height="400"
              src="@/assets/screenshots/screenshot-iphone.png"
            />
          </v-col>
          <v-col cols="12" md="6">
            <v-img
              height="400"
              src="@/assets/screenshots/screenshot-pc.png"
            />
          </v-col>
        </v-row>

        <v-row class="d-none d-lg-flex d-xl-none">
          <v-col cols="12" md="6">
            <v-img
              height="300"
              src="@/assets/screenshots/screenshot-iphone.png"
            />
          </v-col>
          <v-col cols="12" md="6">
            <v-img
              height="300"
              src="@/assets/screenshots/screenshot-pc.png"
            />
          </v-col>
        </v-row>

        <v-row class="d-none d-md-flex d-lg-none">
          <v-col cols="12" md="6">
            <v-img
              height="150"
              src="@/assets/screenshots/screenshot-iphone.png"
            />
          </v-col>
          <v-col cols="12" md="6">
            <v-img
              height="150"
              src="@/assets/screenshots/screenshot-pc.png"
            />
          </v-col>
        </v-row>

        <v-row class="d-flex d-md-none">
          <v-col cols="12" md="6">
            <v-img
              height="200"
              src="@/assets/screenshots/screenshot-iphone.png"
            />
          </v-col>
          <v-col cols="12" md="6">
            <v-img
              height="200"
              src="@/assets/screenshots/screenshot-pc.png"
            />
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
import { mdiDownload, mdiGithub } from '@mdi/js'
</script>
