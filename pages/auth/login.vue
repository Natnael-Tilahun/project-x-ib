<script setup lang="ts">
import { buttonVariants } from "~/components/ui/button";
import { cn } from "@/lib/utils";
import LoginForm from "~/components/login/LoginForm.vue";
import { Separator } from "~/components/ui/separator";
import { Icons } from "~/components/icons";

// Page Meta Configuration
definePageMeta({
  layout: false,
});
const handleBackButton = () => history.back();
</script>

<template>
  <div class="h-full flex flex-col items-center justify-center">
    <!-- Header -->
    <div
      class="w-full h-16 border-b-[1px] flex items-center justify-between px-8"
    >
      <NuxtLink @click="handleBackButton" class="flex gap-2 text-base"
        ><Icons.leftArrow /> Back
      </NuxtLink>
      <NuxtLink to="/auth/register" class="md:text-xl">
        Create an account
      </NuxtLink>
    </div>

    <!-- Body -->
    <div
      class="flex h-full space-y-4 md:space-y-0 flex-col w-full items-center justify-between px-10 py-5 md:p-10"
    >
      <div class="md:space-y-2 space-y-2">
        <img src="/cbe-logo2.png" alt="CBE Logo" />
        <h1 class="md:text-3xl text-2xl font-medium text-center tracking-tight">
          Log in
        </h1>
      </div>

      <div
        class="flex flex-col space-y-4 md:space-y-0 md:flex-row w-full justify-center h-fit"
      >
        <!-- Login Form Section -->

        <div
          class="mx-auto flex py-8 w-full md:w-full justify-center items-center space-y-6 sm:w-[350px]"
        >
          <LoginForm class="xl:w-1/2 md:w-5/6 lg:w-2/3 w-full" />
        </div>

        <div class="relative md:hidden">
          <div class="absolute inset-0 flex items-center">
            <span class="w-full border-t" />
          </div>
          <div class="relative flex justify-center text-xs uppercase">
            <span class="bg-background px-2 text-muted-foreground">
              Or continue with
            </span>
          </div>
        </div>

        <div
          class="w-fit hidden md:flex py-4 gap-8 h-96 items-center justify-between flex-col"
        >
          <Separator
            orientation="vertical"
            class="bg-secondary-foreground basis-2/5 border-2"
          />
          <p class="font-semibold">OR</p>
          <Separator
            class="bg-secondary-foreground basis-2/5 border-2"
            orientation="vertical"
          />
        </div>

        <div
          class="w-full text-center items-center justify-center gap-9 flex-col flex"
        >
          <img src="/qrCode.png" class="w-fit" alt="QR code" />
          <div class="space-y-2">
            <h1 class="md:text-3xl text-2xl font-semibold">
              Log in with QR code
            </h1>
            <p class="md:text-xl text-secondary-foreground">
              Scan this with our App to log in instantly
            </p>
          </div>
        </div>
      </div>

      <!-- Footer -->
      <div class="flex flex-col h-fit self-center gap-4 md:gap-8 text-center">
        <NuxtLink
          to="/forgotPassword"
          class="text-primary font-medium underline"
        >
          Can't login?
        </NuxtLink>
        <div class="space-y-2 text-secondary-foreground text-sm">
          <p>Call 951 for any support</p>
          <NuxtLink href="/"
            >Commercial Bank of Ethiopia <u>Terms</u> & <u>Privacy</u></NuxtLink
          >
        </div>
      </div>
    </div>
  </div>
</template>
