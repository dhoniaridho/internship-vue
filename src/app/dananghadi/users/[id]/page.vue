<script setup lang="ts">
import { useHttp } from '@/composables/http/http'
import { computed } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()

const { data } = useHttp(computed(() => `https://reqres.in/api/users/${route.params.id}`))
</script>

<template>
  <div class="w-full min-h-screen flex justify-center items-center">
    <n-card
      class="container"
      :title="`${data?.data.first_name} ${data?.data.last_name}`"
      style="text-align: center; font-weight: bold"
    >
      <h1>{{ data?.data.email }}</h1>
      <br />
      <n-image :src="`${data?.data.avatar}`"></n-image>
    </n-card>
  </div>
</template>
<style>
.container {
  width: 500px;
  background-color: theme('colors.white');
  border-radius: theme('borderRadius.lg');
  padding: theme('spacing.6');
  box-shadow: theme('boxShadow.xl');
  font-family: Century Gothic;
}
</style>
