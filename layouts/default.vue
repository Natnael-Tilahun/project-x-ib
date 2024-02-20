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

    <!-- Footer -->
    <div class="col-span-full">
      <div
        class="grid lg:grid-cols-4 gap-y-10 grid-cols-2 xl:p-24 gap-4 p-8 md:p-8 lg:p-16 w-full col-span-full"
      >
        <div class="flex flex-col md:px-4 gap-4 lg:gap-8">
          <h1 class="lg:text-2xl text-lg font-bold">Get In Touch</h1>
          <p class="text-secondary-foreground font-medium text-sm">
            Follow our social media channels
          </p>
          <div class="flex items-center gap-4 lg:gap-8">
            <Icons.facebook class="stroke-none" />
            <Icons.twitter class="stroke-none" />
            <Icons.youtube class="stroke-none" />
            <Icons.telegram class="stroke-none" />
          </div>
        </div>
        <div class="flex md:px-4 flex-col gap-4 lg:gap-8">
          <h1 class="lg:text-2xl text-lg font-bold">Company info</h1>
          <ul class="flex flex-col gap-4 lg:gap-6 font-semibold">
            <li class="text-secondary-foreground text-sm">About Us</li>
            <li class="text-secondary-foreground text-sm">Vacancy</li>
            <li class="text-secondary-foreground text-sm">Tenders</li>
            <li class="text-secondary-foreground text-sm">FAQ</li>
          </ul>
        </div>
        <div class="flex md:px-4 flex-col gap-4 lg:gap-8">
          <h1 class="lg:text-2xl font-bold">Services</h1>
          <ul class="flex flex-col gap-4 lg:gap-6 font-semibold">
            <li class="text-secondary-foreground text-sm">Branch Locator</li>
            <li class="text-secondary-foreground text-sm">ATM Locator</li>
            <li class="text-secondary-foreground text-sm">Exchange Rates</li>
            <li class="text-secondary-foreground text-sm">Customer Feedback</li>
          </ul>
        </div>
        <div class="flex md:px-4 flex-col gap-4 lg:gap-8">
          <Icons.appStore />
          <Icons.googlePlay />
        </div>
      </div>
      <div
        class="bg-secondary w-full col-span-full font-semibold flex items-center justify-center p-8"
      >
        <p>@2024 | Commercial Bank of Ethiopia.</p>
      </div>
    </div>
  </div>
</template>
<style scoped>
.router-link-active {
  @apply font-light text-primary bg-popover ml-1;
}
</style>
