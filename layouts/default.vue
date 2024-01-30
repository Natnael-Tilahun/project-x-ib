<script lang="ts" setup>
import { Icons } from "~/components/icons";

const LOCAL_STORAGE_THEME_KEY = "theme";

const route = useRoute();
</script>

<template>
  <div class="bg-background w-full">
    <!-- Header -->
    <div
      class="w-full h-16 lg:h-24 bg-background text-secondary-foreground flex justify-between items-center px-8 lg:px-16"
    >
      <img src="/cbe-logo.png" class="w-40" alt="Logo" />
      <ul class="flex flex-row gap-2.5 lg:gap-8 font-semibold">
        <li>Home</li>
        <li>Terms and Tariff</li>
        <li>About</li>
        <li>Contact Us</li>
      </ul>
      <div class="flex gap-4">
        <UiButton class="font-bold text-foreground" variant="ghost"
          >Register</UiButton
        >
        <UiButton class="font-bold gap-x-2 flex">
          Login
          <Icons.rightArrow
        /></UiButton>
      </div>
    </div>

    <!-- Page Main Content -->
    <div class="space-y-10 p-6 md:px-0 md:py-0 h-full">
      <slot />
    </div>
  </div>
</template>
<style scoped>
.router-link-active {
  @apply font-light text-primary bg-popover ml-1;
}
</style>
