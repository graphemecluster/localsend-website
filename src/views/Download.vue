<template>
  <div class="fill-height pt-md-12">
    <v-row>
      <v-col cols="12">
        <v-img
          height="200"
          src="@/assets/logo-512.png"
        />
      </v-col>
      <v-col cols="12">
        <h1 class="text-h4 text-sm-h2 font-weight-bold text-center">Download LocalSend</h1>
      </v-col>
      <v-col cols="12" class="pt-12 d-flex justify-center flex-wrap">
        <v-btn variant="tonal" size="x-large" class="ma-2" :color="selectedOS === OS.windows ? 'primary' : undefined" @click="selectedOS = OS.windows">
          Windows
        </v-btn>
        <v-btn variant="tonal" size="x-large" class="ma-2" :color="selectedOS === OS.macos ? 'primary' : undefined" @click="selectedOS = OS.macos">
          macOS
        </v-btn>
        <v-btn variant="tonal" size="x-large" class="ma-2" :color="selectedOS === OS.linux ? 'primary' : undefined" @click="selectedOS = OS.linux">
          Linux
        </v-btn>
        <v-btn variant="tonal" size="x-large" class="ma-2" :color="selectedOS === OS.android ? 'primary' : undefined" @click="selectedOS = OS.android">
          Android
        </v-btn>
        <v-btn variant="tonal" size="x-large" class="ma-2" :color="selectedOS === OS.ios ? 'primary' : undefined" @click="selectedOS = OS.ios">
          iOS
        </v-btn>
      </v-col>
      <v-col cols="12">
        <v-row no-gutters>
          <v-col cols="0" md="3">
          </v-col>
          <v-col cols="12" md="6">
            <v-sheet color="grey-lighten-3" class="pa-4" rounded>
              <h1 class="text-h6 text-sm-h6 text-center">{{ selectedOS }} Downloads</h1>

              <v-row no-gutters align="stretch">
                <!-- App Stores -->
                <v-col cols="12" md="4" class="pa-2" v-if="selectedOS !== OS.windows && selectedOS !== OS.linux">
                  <v-sheet color="teal-lighten-4" class="fill-height pa-4" rounded>
                    <h1 class="text-h6 text-sm-h6">App Stores</h1>
                    <p>Recommended for most users.</p>

                    <div v-if="selectedOS === OS.macos || selectedOS === OS.ios">
                      <a href="https://apps.apple.com/us/app/localsend/id1661733229" class="d-block ma-4">
                        <img alt="Download on the App Store" src="@/assets/badges/apple-store-badge.svg" height="64">
                      </a>
                    </div>
                    <div v-else-if="selectedOS === OS.android">
                      <a href='https://play.google.com/store/apps/details?id=org.localsend.localsend_app&pcampaignid=pcampaignidMKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1'>
                        <img alt='Get it on Google Play'
                             src='https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png'
                             height="90"
                             style="z-index: 999"
                        />
                      </a>
                      <a href="https://f-droid.org/packages/org.localsend.localsend_app">
                        <img alt="Download on the App Store" src="@/assets/badges/f-droid-badge.png" height="90">
                      </a>
                    </div>
                  </v-sheet>
                </v-col>

                <!-- Binaries -->
                <v-col cols="12" md="4" class="pa-2" v-if="downloadMetadata[selectedOS].binaries.length !== 0">
                  <v-sheet color="teal-lighten-4 pa-4" class="fill-height" rounded>
                    <h1 class="text-h6 text-sm-h6">Binaries</h1>
                    <p>Download for offline usage.</p>

                    <div v-for="b in downloadMetadata[selectedOS].binaries" class="mt-4">
                      <v-btn variant="tonal" color="teal-darken-4" :prepend-icon="mdiDownload" :href="b.url">
                        {{ b.name }}
                      </v-btn>
                    </div>
                  </v-sheet>
                </v-col>

                <!-- Package Managers -->
                <v-col cols="12" md="4" class="pa-2" v-if="downloadMetadata[selectedOS].packageManagers.length !== 0">
                  <v-sheet color="teal-lighten-4 pa-4" class="fill-height" rounded>
                    <h1 class="text-h6 text-sm-h6">Package Managers</h1>
                    <p>Enjoy automatic updates.</p>

                    <div v-for="p in downloadMetadata[selectedOS].packageManagers" class="mt-4">
                      {{ p.name }}:
                      <v-sheet color="teal-lighten-4">
                        <code>{{ p.command }}</code>
                      </v-sheet>
                    </div>
                  </v-sheet>
                </v-col>
              </v-row>
            </v-sheet>
          </v-col>
          <v-col cols="0" md="3">
          </v-col>
        </v-row>
      </v-col>
      <v-col cols="12" class="d-flex justify-center">
        <v-btn variant="text" size="x-large" class="mt-4" color="primary" :prepend-icon="mdiArrowLeft" to="/">
          Homepage
        </v-btn>
      </v-col>
    </v-row>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { mdiDownload, mdiArrowLeft } from '@mdi/js'

enum OS {
  windows = 'Windows',
  macos = 'MacOS',
  linux = 'Linux',
  android = 'Android',
  ios = 'iOS'
}

const selectedOS = ref<OS>(OS.windows);

interface PackageManager {
  name: string;
  command: string;
}

interface Binaries {
  name: string;
  url: string;
}

interface Download {
  binaries: Binaries[];
  packageManagers: PackageManager[];
}

const downloadMetadata: Record<OS, Download> = {
  [OS.windows]: {
    binaries: [
      {
        name: 'MSIX',
        url: 'https://github.com/localsend/localsend/releases/download/v1.8.0/LocalSend-1.8.0.msix',
      },
      {
        name: 'ZIP (Portable)',
        url: 'https://github.com/localsend/localsend/releases/download/v1.8.0/LocalSend-1.8.0-windows.zip',
      },
    ],
    packageManagers: [
      {
        name: 'Winget',
        command: 'winget install localsend',
      },
      {
        name: 'Scoop',
        command: 'scoop install localsend',
      },
    ],
  },
  [OS.macos]: {
    binaries: [
      {
        name: 'DMG',
        url: 'https://github.com/localsend/localsend/releases/download/v1.8.0/LocalSend-1.8.0.dmg',
      },
    ],
    packageManagers: [
      {
        name: 'Nix',
        command: 'nix-shell -p localsend',
      }
    ],
  },
  [OS.linux]: {
    binaries: [
      {
        name: 'AppImage',
        url: 'https://github.com/localsend/localsend/releases/download/v1.8.0/LocalSend-1.8.0.AppImage',
      }
    ],
    packageManagers: [
      {
        name: 'Flatpak',
        command: 'flatpak install flathub org.localsend.localsend_app',
      },
      {
        name: 'AUR',
        command: 'yay -S localsend-bin',
      },
      {
        name: 'Nix',
        command: 'nix-shell -p localsend',
      },
    ]
  },
  [OS.android]: {
    binaries: [
      {
        name: 'APK',
        url: 'https://github.com/localsend/localsend/releases/download/v1.8.0/LocalSend-1.8.0.apk',
      }
    ],
    packageManagers: [],
  },
  [OS.ios]: {
    binaries: [],
    packageManagers: [],
  }
};

</script>
