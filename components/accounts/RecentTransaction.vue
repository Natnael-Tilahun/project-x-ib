<script lang="ts" setup>
import { Icons } from "../icons";

const transactions: any = [
  {
    description: "description",
    notes: "Notes",
    id: "fdaf342ds34432dsr",
    customerId: "10000000000",
    expenseCategoryId: "Deposit",
    typeId: "Deposit",
    referenceId: "dafads234ar3",
    fromAccountNumber: "100000000000",
    fromAccountBalance: "100000",
    toAccountNumber: "12220002020200",
    toAccountBalance: "200000",
    depositAmount: 6000,
    transactionDate: "Apr 12,2023",
    transactionCurrency: "Birr",
    serviceCharge: "10",
  },
  {
    description: "description",
    notes: "Notes",
    id: "fdaf342ds34432dsr",
    customerId: "10000000000",
    expenseCategoryId: "Deposit",
    typeId: "Deposit",
    referenceId: "dafads234ar3",
    fromAccountNumber: "100000000000",
    fromAccountBalance: "100000",
    toAccountNumber: "12220002020200",
    toAccountBalance: "200000",
    depositAmount: 2000,
    transactionDate: "Apr 12,2023",
    transactionCurrency: "Birr",
    serviceCharge: "10",
  },
  {
    description: "description",
    notes: "Notes",
    id: "fdaf342ds34432dsr",
    customerId: "10000000000",
    expenseCategoryId: "Withdrawal",
    typeId: "Withdrawal",
    referenceId: "dafads234ar3",
    fromAccountNumber: "100000000000",
    fromAccountBalance: "100000",
    toAccountNumber: "12220002020200",
    toAccountBalance: "200000",
    withdrawalAmount: 1000,
    transactionDate: "Apr 14,2023",
    transactionCurrency: "Birr",
    serviceCharge: "10",
  },
  {
    description: "description",
    notes: "Notes",
    id: "fdaf342ds34432dsr",
    customerId: "10000000000",
    expenseCategoryId: "withdraw",
    typeId: "Withdrawal",
    referenceId: "dafads234ar3",
    fromAccountNumber: "100000000000",
    fromAccountBalance: "100000",
    toAccountNumber: "12220002020200",
    toAccountBalance: "200000",
    withdrawalAmount: 1000,
    transactionDate: "Apr 20,2023",
    transactionCurrency: "Birr",
    serviceCharge: "10",
  },
];
</script>

<template>
  <UiCard class="col-span-1 lg:p-8 p-6 gap-5 space-y-6 w-[100%]">
    <div class="flex justify-between items-center">
      <h1 class="font-semibold text-xl">Recent Transactions</h1>
      <NuxtLink to="/transactions" class="text-primary font-medium text-base"
        >View All</NuxtLink
      >
    </div>

    <!-- Deposits -->
    <div v-for="transaction in transactions">
      <div
        class="flex items-center gap-4"
        :key="transaction.id"
        v-if="transaction.typeId == 'Deposit'"
      >
        <Icons.deposit class="w-14 h-14 border-none stroke-none" />
        <div class="flex flex-col gap-1 mr-auto">
          <h1 class="font-medium text-base">{{ transaction.typeId }}</h1>
          <p class="font-light">{{ transaction.transactionDate }}</p>
        </div>
        <p class="text-[#2DD683] font-medium">
          + {{ transaction.depositAmount }}
          {{ transaction.transactionCurrency }}
        </p>
      </div>

      <!-- Withdrawal -->
      <div
        class="flex items-center gap-4"
        :key="transaction.id"
        v-if="transaction.typeId === 'Withdrawal'"
      >
        <Icons.withdraw class="w-14 h-14 border-none stroke-none" />
        <div class="flex flex-col gap-1 mr-auto">
          <h1 class="font-medium text-base">{{ transaction.typeId }}</h1>
          <p class="font-light">{{ transaction.transactionDate }}</p>
        </div>
        <p class="text-[#E74A51] font-medium">
          - {{ transaction.withdrawalAmount }}
          {{ transaction.transactionCurrency }}
        </p>
      </div>
    </div>
  </UiCard>
</template>

<style lang="postcss" scoped></style>
