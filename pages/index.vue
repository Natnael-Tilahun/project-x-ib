<script setup lang="ts">
import DashboardDateRangePicker from "~/components/dashboard/DateRangePicker.vue";
import { Icons } from "~/components/icons";

const route = useRoute();
</script>

<template>
  <div
    class="flex flex-col h-fit md:h-screen xl:h-full w-full md:justify-evenly"
  >
    <div
      class="md:grid flex flex-col gap-28 lg:gap-20 xl:gap-40 p-8 py-20 md:py-16 lg:p-20 xl:p-32 lg:py-32 h-fit md:h-full xl:py-20 xl:h-screen lg:grid-rows-6 grid-cols-1 md:grid-cols-2"
    >
      <div
        class="flex flex-col md:h-full h-fit order-last md:order-first md:row-start-2 row-span-full gap-6 lg:gap-10"
      >
        <div class="space-y-2">
          <h1
            class="font-extrabold text-xl lg:text-5xl xl:text-6xl tracking-wider leading-relaxed"
          >
            Digital Banking portal
          </h1>
          <p
            class="font-medium text-base lg:text-xl lg:tracking-widest text-secondary-foreground"
          >
            Empowering Your Finances, Anytime, Anywhere. Seamless Banking in the
            Digital Era.
          </p>
        </div>

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
        class="md:relative flex flex-col justify-center md:justify-start items-center md:items-start md:row-span-full lg:row-start-1 w-full h-60 md:h-full"
      >
        <img src="/spiralsvg.png" class="absolute z-0 h-96 md:h-fit" alt="" />
        <img
          src="/mobile_banking.png"
          class="z-50 absolute h-96 md:h-fit"
          alt=""
        />
      </div>
    </div>
  </div>
</template>
