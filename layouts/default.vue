<script lang="ts" setup>
import { Icons } from "~/components/icons";

const LOCAL_STORAGE_THEME_KEY = "theme";

const route = useRoute();
</script>

<template>
  <div class="bg-background w-full">
    <!-- Header -->
    <div
      class="w-full h-16 lg:h-24 bg-background text-secondary-foreground flex justify-between items-center px-4 md:px-8 lg:px-16"
    >
      <img src="/cbe-logo.png" class="w-40" alt="Logo" />
      <ul class="md:flex hidden flex-row gap-2.5 lg:gap-8 font-semibold">
        <NuxtLink to="/">Home</NuxtLink>
        <NuxtLink to="/terms-and-tariff">Terms and Tariff</NuxtLink>
        <NuxtLink to="/about">About</NuxtLink>
        <NuxtLink to="/contact-us">Contact Us</NuxtLink>
      </ul>
      <div class="flex gap-4">
        <NuxtLink to="/auth/register">
          <UiButton class="font-bold text-foreground" variant="ghost"
            >Register</UiButton
          ></NuxtLink
        >

        <NuxtLink to="/auth/login">
          <UiButton class="font-bold gap-x-2 flex">
            Login
            <Icons.rightArrow /></UiButton
        ></NuxtLink>
      </div>
    </div>

    <!-- Page Main Content -->
    <div class="space-y-10 py-6 md:px-0 md:py-0 h-full">
      <slot />
    </div>
  </div>
</template>
<style scoped>
.router-link-active {
  @apply font-light text-primary bg-popover ml-1;
}
</style>
