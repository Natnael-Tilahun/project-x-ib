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
        class="flex flex-col h-full md:row-start-2 row-span-full gap-4 lg:gap-8"
      >
        <h1
          class="font-extrabold md:text-xl lg:text-5xl xl:text-6xl leading-snug tracking-wider"
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
          <UiButton size="lg" class="font-bold rounded-full">
            Register Now
          </UiButton>
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
            <Icons.facebook />
            <Icons.twitter />
            <Icons.youtube />
            <Icons.telegram />
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
