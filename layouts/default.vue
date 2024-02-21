<script lang="ts" setup>
import { Icons } from "~/components/icons";

const LOCAL_STORAGE_THEME_KEY = "theme";

const route = useRoute();

const handleNavigation = (path: string) => {
  navigateTo(path);
};
</script>

<template>
  <div class="bg-background w-full">
    <!-- Header -->
    <div
      class="w-full h-16 lg:h-20 border-b-[1px] gap-4 bg-background text-secondary-foreground flex justify-between items-center px-4 md:px-8 lg:px-16"
    >
      <!-- Mobile Menu -->
      <UiSheet class="lg:hidden">
        <UiSheetTrigger class="lg:hidden">
          <Icons.menu class="w-6 h-6" />
        </UiSheetTrigger>
        <UiSheetContent side="left">
          <ul
            class="flex flex-col lg:hidden py-0 gap-6 lg:gap-8 text-[#AFAFAF] font-medium text-base"
          >
            <img src="/cbe-logo.png" class="w-fit" alt="Logo" />

            <li
              :class="[
                route.path == '/'
                  ? 'flex gap-2.5 text-base whitespace-nowrap text-primary border-l-2 border-primary'
                  : 'flex gap-2.5 text-base  whitespace-nowrap',
              ]"
              class="px-4"
              @click="handleNavigation('/')"
            >
              <UiSheetClose class="flex gap-2 items-center w-full">
                <Icons.accounts class="w-4 h-4" />Home</UiSheetClose
              >
            </li>

            <li
              class="px-4"
              :class="[
                route.path == '/terms-and-tariff'
                  ? 'flex gap-2.5 text-base whitespace-nowrap text-primary border-l-2 border-primary'
                  : 'flex gap-2.5 text-base  whitespace-nowrap',
              ]"
              @click="handleNavigation('/terms-and-tariff')"
            >
              <UiSheetClose class="flex gap-2 items-center w-full">
                <Icons.transactions
                  :class="[
                    route.path == '/terms-and-tariff'
                      ? 'fill-primary stroke-primary'
                      : '',
                  ]"
                  class="w-4 h-4"
                />Terms and Tariff
              </UiSheetClose>
            </li>

            <li
              class="px-4"
              :class="[
                route.path == '/about'
                  ? 'flex gap-2.5 text-base whitespace-nowrap text-primary border-l-2 border-primary'
                  : 'flex gap-2.5 text-base  whitespace-nowrap',
              ]"
              @click="handleNavigation('/about')"
            >
              <UiSheetClose class="flex gap-2 items-center w-full">
                <Icons.statement
                  :class="[route.path == '/about' ? 'fill-primary' : '']"
                  class="w-4 h-4"
                />
                About
              </UiSheetClose>
            </li>
            <li
              class="px-4"
              :class="[
                route.path == '/contact-us'
                  ? 'flex gap-2.5 text-base whitespace-nowrap text-primary border-l-2 stroke-primary border-primary'
                  : 'flex gap-2.5 text-base  whitespace-nowrap',
              ]"
              @click="handleNavigation('/contact-us')"
            >
              <UiSheetClose class="flex gap-2 items-center w-full">
                <Icons.activity
                  :class="[route.path == '/contact-us' ? 'fill-primary' : '']"
                  class="w-4 h-4"
                />
                Contact Us
              </UiSheetClose>
            </li>
            <UiSelect default-value="English">
              <UiSelectTrigger class="w-full md:hidden">
                <UiSelectValue placeholder="Language" />
              </UiSelectTrigger>
              <UiSelectContent>
                <UiSelectGroup>
                  <UiSelectItem value="English"> English </UiSelectItem>
                  <UiSelectItem value="Amharic"> Amharic </UiSelectItem>
                  <UiSelectItem value="Oromic"> Oromic </UiSelectItem>
                  <UiSelectItem value="Tigray"> Tigray </UiSelectItem>
                </UiSelectGroup>
              </UiSelectContent>
            </UiSelect>
          </ul>
        </UiSheetContent>
      </UiSheet>
      <img src="/cbe-logo.png" class="w-40 hidden lg:block" alt="Logo" />

      <ul class="lg:flex hidden flex-row gap-2.5 lg:gap-8 font-semibold">
        <NuxtLink to="/">Home</NuxtLink>
        <NuxtLink to="https://combanketh.et/en/terms-and-tariff" target="_blank"
          >Terms and Tariff</NuxtLink
        >
        <NuxtLink to="/about">About</NuxtLink>
        <NuxtLink to="/contact-us">Contact Us</NuxtLink>
      </ul>

      <div class="flex gap-4 lg:gap-8">
        <UiSelect default-value="English">
          <UiSelectTrigger class="w-full hidden md:flex">
            <UiSelectValue placeholder="Language" />
          </UiSelectTrigger>
          <UiSelectContent>
            <UiSelectGroup>
              <UiSelectItem value="English"> English </UiSelectItem>
              <UiSelectItem value="Amharic"> Amharic </UiSelectItem>
              <UiSelectItem value="Oromic"> Oromic </UiSelectItem>
              <UiSelectItem value="Tigray"> Tigray </UiSelectItem>
            </UiSelectGroup>
          </UiSelectContent>
        </UiSelect>
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
        <div class="flex flex-col md:px-4 gap-4">
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
        <div class="flex md:px-4 flex-col gap-4">
          <h1 class="lg:text-2xl text-lg font-bold">Company info</h1>
          <ul class="flex flex-col gap-4 font-semibold">
            <li class="text-secondary-foreground text-sm">About Us</li>
            <li class="text-secondary-foreground text-sm">Vacancy</li>
            <li class="text-secondary-foreground text-sm">Tenders</li>
            <li class="text-secondary-foreground text-sm">FAQ</li>
          </ul>
        </div>
        <div class="flex md:px-4 flex-col gap-4">
          <h1 class="lg:text-2xl font-bold">Services</h1>
          <ul class="flex flex-col gap-4 font-semibold">
            <li class="text-secondary-foreground text-sm">Branch Locator</li>
            <li class="text-secondary-foreground text-sm">ATM Locator</li>
            <li class="text-secondary-foreground text-sm">Exchange Rates</li>
            <li class="text-secondary-foreground text-sm">Customer Feedback</li>
          </ul>
        </div>
        <div class="flex md:px-4 flex-col gap-4 lg:gap-6">
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
  @apply text-background p-2 rounded-lg bg-primary;
}
</style>
