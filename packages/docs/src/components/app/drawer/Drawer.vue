<template>
  <v-navigation-drawer
    id="app-drawer"
    v-model="app.drawer"
    width="300"
  >
    <template #append>
      <v-divider />

      <div class="text-medium-emphasis text-caption py-2 px-3 d-flex align-center">
        <div class="d-inline-flex align-center">
          <v-icon start>mdi-label</v-icon>
          Latest release:
        </div>

        <v-btn
          density="compact"
          class="text-none px-2 ms-auto"
          variant="text"
        >
          v{{ version }}

          <v-icon size="xs" end>mdi-open-in-new</v-icon>
        </v-btn>
      </div>
    </template>

    <app-list :items="app.items" nav>
      <template #divider>
        <v-divider class="my-3 mb-4 ms-16" />
      </template>
    </app-list>
  </v-navigation-drawer>
</template>

<script setup>
  // Components
  import AppList from '@/components/app/list/List.vue'

  // Composables
  import { useAppStore } from '@/store/app'

  // Utilities
  import { onMounted } from 'vue'
  import { version } from 'vuetify'
  import { wait } from '@/util/helpers'

  const app = useAppStore()

  onMounted(async () => {
    await wait(1000)

    const element = document.querySelector('#app-drawer .v-list-item--active:not(.v-list-group__header)')

    if (!element) return

    element.scrollIntoView({
      behavior: 'smooth',
      block: 'center',
      inline: 'center',
    })
  })
</script>
