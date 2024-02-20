<script setup lang="ts">
import DashboardDateRangePicker from "~/components/dashboard/DateRangePicker.vue";
import { Icons } from "~/components/icons";

const route = useRoute();
</script>

<template>
  <div class="flex flex-col md:h-screen xl:h-full w-full justify-evenly">
    <div
      class="grid md:gap-10 lg:gap-20 xl:gap-40 p-8 py-20 md:py-16 lg:p-20 xl:p-32 lg:py-32 h-full xl:py-20 xl:h-screen lg:grid-rows-6 grid-cols-1 md:grid-cols-2"
    >
      <div
        class="flex flex-col h-full md:row-start-2 row-span-full gap-4 lg:gap-10"
      >
        <h1
          class="font-extrabold md:text-xl lg:text-5xl xl:text-6xl tracking-wider leading-relaxed"
        >
          Digital Banking portal
        </h1>
        <p
          class="font-medium text-sm lg:text-xl lg:tracking-widest text-secondary-foreground"
        >
          Empowering Your Finances, Anytime, Anywhere. Seamless Banking in the
          Digital Era.
        </p>
        <div class="flex gap-2.5">
          <NuxtLink to="/auth/register">
            <UiButton size="lg" class="font-bold rounded-full">
              Register Now
            </UiButton>
          </NuxtLink>

          <UiButton
            variant="ghost"
            size="lg"
            class="font-bold border-primary border-[1px] rounded-full"
          >
            Learn More
          </UiButton>
        </div>
      </div>

      <div
        class="relative md:block hidden row-span-full lg:row-start-1 w-full h-full"
      >
        <img src="/spiralsvg.png" class="absolute z-0" alt="" />
        <img src="/mobile_banking.png" class="z-50 absolute -top-12" alt="" />
      </div>
    </div>
  </div>
</template>
