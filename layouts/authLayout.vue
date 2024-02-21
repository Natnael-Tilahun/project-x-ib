<script lang="ts" setup>
import { Icons } from "~/components/icons";

const LOCAL_STORAGE_THEME_KEY = "theme";

const route = useRoute();

const handleNavigation = (path: string) => {
  navigateTo(path);
};
</script>

<template>
  <div class="bg-background min-h-screen w-full">
    <!-- Header -->
    <div
      class="w-full h-16 lg:h-20 border-b-[1px] bg-background text-secondary-foreground gap-6 flex justify-between items-center px-6 md:px-8 lg:px-16"
    >
      <img src="/cbe-logo.png" class="w-40 hidden lg:block" alt="Logo" />

      <!-- Mobile Menu -->
      <UiSheet class="lg:hidden">
        <UiSheetTrigger>
          <Icons.menu class="w-6 h-6 lg:hidden" />
        </UiSheetTrigger>
        <UiSheetContent side="left">
          <ul
            class="flex flex-col py-0 gap-6 lg:gap-8 text-[#AFAFAF] font-medium text-base"
          >
            <img src="/cbe-logo.png" class="w-fit" alt="Logo" />

            <li
              :class="[
                route.path == '/accounts'
                  ? 'flex gap-2.5 text-base whitespace-nowrap text-primary border-l-2 border-primary'
                  : 'flex gap-2.5 text-base  whitespace-nowrap',
              ]"
              class="px-4"
              @click="handleNavigation('/accounts')"
            >
              <UiSheetClose class="flex gap-2 items-center w-full">
                <Icons.accounts class="w-4 h-4" />Accounts</UiSheetClose
              >
            </li>

            <li
              class="px-4"
              :class="[
                route.path == '/transactions'
                  ? 'flex gap-2.5 text-base whitespace-nowrap text-primary border-l-2 border-primary'
                  : 'flex gap-2.5 text-base  whitespace-nowrap',
              ]"
              @click="handleNavigation('/transactions')"
            >
              <UiSheetClose class="flex gap-2 items-center w-full">
                <Icons.transactions
                  :class="[
                    route.path == '/transactions'
                      ? 'fill-primary stroke-primary'
                      : '',
                  ]"
                  class="w-4 h-4"
                />Transactions
              </UiSheetClose>
            </li>

            <li
              class="px-4"
              :class="[
                route.path == '/statement'
                  ? 'flex gap-2.5 text-base whitespace-nowrap text-primary border-l-2 border-primary'
                  : 'flex gap-2.5 text-base  whitespace-nowrap',
              ]"
              @click="handleNavigation('/statement')"
            >
              <UiSheetClose class="flex gap-2 items-center w-full">
                <Icons.statement
                  :class="[route.path == '/statement' ? 'fill-primary' : '']"
                  class="w-4 h-4"
                />
                Statement
              </UiSheetClose>
            </li>
            <li
              class="px-4"
              :class="[
                route.path == '#'
                  ? 'flex gap-2.5 text-base whitespace-nowrap text-primary border-l-2 stroke-primary border-primary'
                  : 'flex gap-2.5 text-base  whitespace-nowrap',
              ]"
              @click="handleNavigation('#')"
            >
              <UiSheetClose class="flex gap-2 items-center w-full">
                <Icons.activity
                  :class="[route.path == '/#' ? 'fill-primary' : '']"
                  class="w-4 h-4"
                />
                Activity
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

      <!-- Large Screen Menu -->
      <ul
        class="lg:flex hidden flex-row gap-2.5 lg:gap-8 text-[#AFAFAF] font-medium text-base"
      >
        <NuxtLink class="flex gap-2 items-center" to="/accounts"
          ><Icons.accounts class="w-4 h-4" /> Accounts</NuxtLink
        >
        <NuxtLink class="flex gap-2 items-center" to="/transactions">
          <Icons.transactions class="w-4 h-4" /> Transactions</NuxtLink
        >
        <NuxtLink class="flex gap-2 items-center" to="/statement"
          ><Icons.statement class="w-4 h-4" /> Statement</NuxtLink
        >
        <NuxtLink class="flex gap-2 items-center" to="/activity">
          <Icons.activity class="w-4 h-4" /> Activity</NuxtLink
        >
      </ul>

      <div class="flex items-center gap-5">
        <UiSelect default-value="English">
          <UiSelectTrigger class="w-[100px] hidden md:flex">
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
        <UiSheet>
          <UiSheetTrigger>
            <NuxtLink to="/notifications">
              <Icons.notification class="w-8 h-8 stroke-none" /> </NuxtLink
          ></UiSheetTrigger>
          <UiSheetContent> <NotificationsList /> </UiSheetContent>
        </UiSheet>

        <NuxtLink to="/settings">
          <Icons.settings class="w-8 h-8 stroke-none" />
        </NuxtLink>

        <UiAvatar class="h-11 w-11">
          <UiAvatarImage src="avatars/01.png" alt="User Profile" />
          <UiAvatarFallback>SC</UiAvatarFallback>
        </UiAvatar>
      </div>
    </div>

    <!-- Page Main Content -->
    <div class="space-y-10 h-full md:py-8 px-6 md:px-4 lg:px-16">
      <slot />
    </div>

    <!-- Footer -->
    <hr class="m-4 md:mx-8 lg:mx-16 print-hide" />
    <div
      class="border--[1px] w-full gap-4 md:gap-14 text-sm flex flex-col md:flex-row items-center p-8 px-4 md:px-8 lg:px-16 print-hide"
    >
      <p class="text-secondary-foreground text-sm">
        @2024 | Commercial Bank of Ethiopia.
      </p>
      <ul class="flex gap-6 items-center md:mr-auto">
        <li class="text-secondary-foreground">Help</li>
        <li class="text-secondary-foreground">Privacy</li>
        <li class="text-secondary-foreground">Terms</li>
      </ul>
      <div class="flex items-center gap-4 lg:gap-8">
        <Icons.socialMediaFacebook class="w-5 h-5 stroke-none" />
        <Icons.socialMediaTwitter class="w-5 h-5 stroke-none" />
        <Icons.socialMediaInstagram class="w-5 h-5 stroke-none" />
      </div>
    </div>
  </div>
</template>
<style scoped>
.router-link-active {
  @apply text-background p-2 rounded-lg bg-primary w-full;
}
</style>
