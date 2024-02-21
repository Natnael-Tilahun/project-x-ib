<script lang="ts" setup>
import { Icons } from "~/components/icons";

definePageMeta({
  layout: "auth-layout",
});
</script>

<template>
  <div
    class="w-full grid md:gap-4 lg:gap-20 grid-cols-1 md:grid-cols-2 lg:px-8"
  >
    <div class="space-y-10 flex flex-col justify-between items-baseline h-full">
      <!-- Account list and balance -->
      <AccountsAccountLists />

      <!--  Transactions Overview -->
      <AccountsOverview />
    </div>

    <div class="w-full place-items-end flex flex-col gap-7 items-end">
      <!-- Quick Transfer -->
      <AccountsQuickTransfer />

      <!-- Applications -->
      <AccountsApplications />

      <!-- Recent Transactions -->
      <AccountsRecentTransaction />
    </div>
  </div>
</template>
