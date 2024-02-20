<script setup lang="ts">
import { ref } from "vue";
import { cn } from "@/lib/utils";
import { useForm } from "vee-validate";
import "vue-tel-input/vue-tel-input.css";

import { Icons } from "../icons";
const store = useAuthStore();
const isLoading = ref(false);
</script>

<template>
  <div class="space-y-4 flex justify-center flex-col items-center w-full">
    <img src="/cbeanimate.png" alt="cbe animation" />
    <h1 class="text-2xl md:text-4xl font-medium text-center tracking-wide">
      Success
    </h1>
    <p class="md:text-lg text-sm tracking-wide text-secondary-foreground">
      Your have Successfully registered for the service please visit nearby
      branch for activation.
    </p>
  </div>
  <UiButton
    size="lg"
    class="hover:bg-fuchsia-800 font-light tracking-wider gap-10 w-full text-xl rounded-xl h-14"
  >
    Check Near By CBE Branches on Map
    <Icons.ping />
  </UiButton>
</template>
