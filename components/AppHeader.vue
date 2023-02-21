<script setup lang="ts">
const client = useSupabaseAuthClient()
const user = useSupabaseUser()
const colorMode = useColorMode()

const toggleDark = () => {
  colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark'
}

const colorModeIcon = computed(() => colorMode.preference === 'dark' ? 'heroicons-outline:moon' : 'heroicons-outline:sun')

const logout = async () => {
  await client.auth.signOut()
  navigateTo('/')
}
</script>

<template>
  <div>
    <Title>TodoApp TA-20V Daniel Girtsis</Title>
    <div class="flex items-center md:justify-between justify-center">
      <div class="hidden md:block">
        
        />
      </div>
      <div class="flex items-center">
        <UButton variant="transparent" :icon="colorModeIcon" @click="toggleDark" />
        <UButton v-if="user" class="u-text-white" variant="transparent" @click="logout">
          Logout
        </UButton>
      </div>
    </div>
  </div>
</template>
