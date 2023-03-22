<template>
  <v-app>
    <v-main>
      <router-view />
      <v-footer class="pa-0">
        <v-row no-gutters>
          <v-col cols="12">
            <v-sheet color="grey-lighten-4" class="d-flex justify-end">
              <v-btn variant="plain" to="/privacy">Privacy</v-btn>
              <v-btn variant="plain" to="/contact">Contact</v-btn>
            </v-sheet>
          </v-col>
        </v-row>
      </v-footer>
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
  //
</script>
