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
const isSuccessful = ref(false);
const handleSuccess = () => {
  isSuccessful.value = !isSuccessful.value;
};
</script>

<template>
  <div class="h-screen flex flex-col items-center justify-center">
    <!-- Header -->
    <div
      class="w-full h-16 border-b-[1px] flex items-center justify-between px-8"
    >
      <NuxtLink @click="handleBackButton" class="flex gap-2 text-base"
        ><Icons.leftArrow /> Back
      </NuxtLink>
      <NuxtLink to="/auth/login" class="md:text-xl"> Login </NuxtLink>
    </div>

    <!-- Body -->
    <div
      class="flex h-full md:w-2/3 lg:w-1/2 xl:w-2/5 flex-col text-center gap-10 items-center px-10 py-10 md:py-20"
    >
      <RegisterSuccess v-if="isSuccessful" />

      <RegisterForm v-else class="w-full" :handleSuccess="handleSuccess" />
    </div>
  </div>
</template>
