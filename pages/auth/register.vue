<script setup lang="ts">
import { buttonVariants } from "~/components/ui/button";
import { cn } from "@/lib/utils";
import LoginForm from "~/components/login/LoginForm.vue";
import { Separator } from "~/components/ui/separator";
import { Icons } from "~/components/icons";
import RegisterForm from "~/components/register/RegisterForm.vue";

// Page Meta Configuration
definePageMeta({
  layout: false,
});

const handleBackButton = () => history.back();
</script>

<template>
  <div class="h-screen flex flex-col items-center justify-center">
    <!-- Header -->
    <div
      class="w-full h-20 border-b-[1px] flex items-center justify-between px-8"
    >
      <NuxtLink @click="handleBackButton" class="flex gap-2"
        ><Icons.leftArrow /> Back
      </NuxtLink>
      <NuxtLink to="/auth/login" class="text-xl"> Login </NuxtLink>
    </div>

    <!-- Body -->
    <div
      class="flex h-full md:w-1/2 lg:w-2/5 flex-col text-center gap-10 items-center px-10 py-10 md:py-20"
    >
      <!-- <div class="space-y-4 w-full">
        <h1 class="text-2xl md:text-4xl font-medium text-center tracking-wide">
          Sign UP
        </h1>
        <p class="md:text-lg text-sm tracking-wide text-secondary-foreground">
          Sign Up to Commercial Bank of Ethiopia Digital Banking platform to
          elevate your banking experience, roviding you with a secure,
          efficient, and user-friendly interface that puts you in control of
          your finances and business.
        </p>
      </div> -->
      <!-- <div class="w-full space-y-6">
        <h3 class="text-base text-foreground">
          Enter Your Mobile Banking Service Activated Phone
        </h3>
      </div> -->
      <RegisterSuccess />

      <!-- <RegisterForm class="w-full" /> -->
    </div>
  </div>
</template>
