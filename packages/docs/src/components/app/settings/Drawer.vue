<template>
  <v-navigation-drawer
    id="settings-drawer"
    v-model="app.settings"
    :location="isRtl ? 'left' : 'right'"
    :scrim="false"
    disable-route-watcher
    position="fixed"
    temporary
    touchless
    width="350"
  >
    <v-toolbar flat>
      <v-toolbar-title text="Settings" class="ps-0" />

      <template #append>
        <v-btn
          icon="mdi-close"
          variant="flat"
          @click="app.settings = false"
        />
      </template>
    </v-toolbar>

    <v-divider />

    <v-container>
      <app-settings-theme />

      <v-divider class="mt-4 mb-3 mx-n3" />

      <app-settings-rtl />

      <v-divider class="mt-4 mb-3 mx-n3" />

      <app-settings-api />

      <v-divider class="mt-4 mb-3 mx-n3" />

      <app-settings-dev />
    </v-container>
  </v-navigation-drawer>
</template>

<script setup>
  // Components
  import AppSettingsApi from './Api.vue'
  import AppSettingsRtl from './Rtl.vue'
  import AppSettingsTheme from './Theme.vue'
  import AppSettingsDev from './Dev.vue'

  // Composables
  import { useAppStore } from '@/store/app'
  import { useRtl } from 'vuetify'

  const { isRtl } = useRtl()
  const app = useAppStore()
</script>
