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
    id: "fdaf342ds34432dsa",
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
    id: "fdaf342ds34ad2dsr",
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
    id: "fdaf342dads432dsr",
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
  <div class="md:space-y-14 space-y-6 w-full">
    <div class="flex md:w-2/3 items-center self-start gap-6">
      <UiInput placeholder="Search here" class="h-10 w-full bg-white" />
      <Icons.filter />
    </div>
    <UiAccordion
      v-for="transaction in transactions"
      class="w-full"
      type="single"
      collapsible
    >
      <UiAccordionItem
        :key="transaction.id"
        v-if="transaction.typeId == 'Deposit'"
        :value="transaction.id"
      >
        <UiAccordionTrigger
          class="flex items-center md:gap-8 gap-4 hover:no-underline"
        >
          <Icons.deposit class="w-14 h-14 border-none stroke-none" />
          <div class="flex flex-col md:gap-1 mr-auto text-left">
            <h1 class="text-[#2DD683] font-bold text-lg">
              {{ transaction.depositAmount }}
              {{ transaction.transactionCurrency }}
            </h1>
            <p class="font-normal text-sm text-[#AFAFAF]">
              {{ transaction.typeId }}
            </p>
          </div>
          <p class="text-sm text-[#AFAFAF] font-normal">
            {{ transaction.transactionDate }}
          </p>
        </UiAccordionTrigger>
        <UiAccordionContent
          class="md:px-16 px-4 md:py-8 py-6 w-full shadow-md rounded-xl border-b-0"
        >
          <div
            class="flex flex-col md:flex-row items-center gap-4 justify-between w-full"
          >
            <ul class="ms:space-y-4 space-y-2 w-full text-xs md:text-sm">
              <li class="grid grid-cols-2 md:w-[65%] w-full md:gap-8 gap-4">
                <h1 class="font-bold">Transaction Type:</h1>
                <p>Mobile Money TXN</p>
              </li>
              <li class="grid grid-cols-2 md:w-[65%] w-full md:gap-8 gap-4">
                <h1 class="font-bold">Transaction ID:</h1>
                <p>FT2405456M9D2</p>
              </li>
              <li class="grid grid-cols-2 md:w-[65%] w-full md:gap-8 gap-4">
                <h1 class="font-bold">Done Via:</h1>
                <p>Transfer Done Via Branch</p>
              </li>
              <li class="grid grid-cols-2 md:w-[65%] w-full md:gap-8 gap-4">
                <h1 class="font-bold">Transferred From:</h1>
                <p>Txn FT2405456M9D2</p>
              </li>
              <li class="grid grid-cols-2 md:w-[65%] w-full md:gap-8 gap-4">
                <h1 class="font-bold">Transfer Amount:</h1>
                <p>28,000.00 Birr</p>
              </li>
              <li class="grid grid-cols-2 md:w-[65%] w-full md:gap-8 gap-4">
                <h1 class="font-bold">Commission:</h1>
                <p>0.00 Birr</p>
              </li>
            </ul>
            <img src="/qrCode.png" class="w-fit block" alt="qrcode" />
          </div>
        </UiAccordionContent>
      </UiAccordionItem>

      <UiAccordionItem
        :key="transaction.id"
        v-if="transaction.typeId === 'Withdrawal'"
        :value="transaction.id"
      >
        <UiAccordionTrigger class="flex items-center gap-8">
          <Icons.withdraw class="w-14 h-14 border-none stroke-none" />
          <div class="flex flex-col gap-1 mr-auto text-left">
            <h1 class="text-[#E74A51] font-bold text-lg">
              {{ transaction.withdrawalAmount }}
              {{ transaction.transactionCurrency }}
            </h1>
            <p class="font-normal text-sm text-[#AFAFAF]">
              {{ transaction.typeId }}
            </p>
          </div>
          <p class="text-sm text-[#AFAFAF] font-normal">
            {{ transaction.transactionDate }}
          </p>
        </UiAccordionTrigger>
        <UiAccordionContent
          class="md:px-16 px-8 py-8 w-full shadow-md rounded-xl border-b-0"
        >
          <div
            class="flex flex-col md:flex-row items-center gap-4 justify-between w-full"
          >
            <ul class="space-y-4 w-full">
              <li class="grid grid-cols-2 md:w-[65%] w-full gap-8">
                <h1 class="font-bold">Transaction Type:</h1>
                <p>Mobile Money TXN</p>
              </li>
              <li class="grid grid-cols-2 md:w-[65%] w-full gap-8">
                <h1 class="font-bold">Transaction ID:</h1>
                <p>FT2405456M9D2</p>
              </li>
              <li class="grid grid-cols-2 md:w-[65%] w-full gap-8">
                <h1 class="font-bold">Done Via:</h1>
                <p>Transfer Done Via Branch</p>
              </li>
              <li class="grid grid-cols-2 md:w-[65%] w-full gap-8">
                <h1 class="font-bold">Transferred From:</h1>
                <p>Txn FT2405456M9D2</p>
              </li>
              <li class="grid grid-cols-2 md:w-[65%] w-full gap-8">
                <h1 class="font-bold">Transfer Amount:</h1>
                <p>28,000.00 Birr</p>
              </li>
              <li class="grid grid-cols-2 md:w-[65%] w-full gap-8">
                <h1 class="font-bold">Commission:</h1>
                <p>0.00 Birr</p>
              </li>
            </ul>
            <img src="/qrCode.png" class="w-fit block" alt="qrcode" />
          </div>
        </UiAccordionContent>
      </UiAccordionItem>
    </UiAccordion>
  </div>
</template>

<style lang="postcss" scoped></style>
