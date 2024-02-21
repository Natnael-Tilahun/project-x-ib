<script setup lang="ts">
import {
  VisArea,
  VisAxis,
  VisDonut,
  VisSingleContainer,
  VisStackedBar,
  VisXYContainer,
} from "@unovis/vue";
import { Icons } from "~/components/icons";

type Data = (typeof data)[number];
interface DataRecord {
  name: string;
  total: number | string;
}
const data = [
  { name: "Jan", total: Math.floor(Math.random() * 5000) + 1000 },
  { name: "Feb", total: Math.floor(Math.random() * 5000) + 1000 },
  { name: "Mar", total: Math.floor(Math.random() * 5000) + 1000 },
  { name: "Apr", total: Math.floor(Math.random() * 5000) + 1000 },
  { name: "May", total: Math.floor(Math.random() * 5000) + 1000 },
  { name: "Jun", total: Math.floor(Math.random() * 5000) + 1000 },
  { name: "Jul", total: Math.floor(Math.random() * 5000) + 1000 },
  { name: "Aug", total: Math.floor(Math.random() * 5000) + 1000 },
  { name: "Sep", total: Math.floor(Math.random() * 5000) + 1000 },
  { name: "Oct", total: Math.floor(Math.random() * 5000) + 1000 },
  { name: "Nov", total: Math.floor(Math.random() * 5000) + 1000 },
  { name: "Dec", total: Math.floor(Math.random() * 5000) + 1000 },
];

const x = (d: DataRecord, i: number) => i;
const value = (d: DataRecord) =>
  typeof d.total === "string" ? parseInt(d.total.replace(/\D/g, "")) : d.total;

// const value = (d: number) => d.total;

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
    amount: 6000,
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
    amount: 2000,
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
    amount: 1000,
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
  <UiCard class="p-6 space-y-8 w-full text-[#AFAFAF]">
    <div class="flex flex-col lg:flex-row items-center gap-4 lg:gap-8">
      <h1 class="font-semibold text-xl mr-auto text-foreground">
        Transaction Statistics
      </h1>

      <UiSelect default-value="1">
        <UiSelectTrigger class="lg:w-[200px] w-full">
          <div class="flex gap-2">
            <Icons.calender />
            <UiSelectValue placeholder="Time" />
          </div>
        </UiSelectTrigger>
        <UiSelectContent>
          <UiSelectGroup>
            <UiSelectItem value="12"> Annual </UiSelectItem>
            <UiSelectItem value="6"> Semi-Annual </UiSelectItem>
            <UiSelectItem value="4"> Quarterly </UiSelectItem>
            <UiSelectItem value="1"> 1 Month </UiSelectItem>
          </UiSelectGroup>
        </UiSelectContent>
      </UiSelect>
    </div>

    <div
      class="flex flex-col lg:flex-row lg:h-40 items-center gap-4 lg:gap-10 w-full lg:px-10"
    >
      <div class="lg:w-1/4 h-fit">
        <VisSingleContainer class="h-40 w-full" :data="data">
          <VisDonut :value="value" />
        </VisSingleContainer>
      </div>

      <ul class="flex flex-col gap-2 py-4 lg:py-0 w-full">
        <li class="flex items-center gap-4">
          <UiBadge class="rounded-full bg-primary w-2 mx-2 p-1 h-1"></UiBadge>
          Mobile Transfer
        </li>
        <li class="flex items-center gap-4">
          <UiBadge
            class="rounded-full bg-foreground w-2 mx-2 p-1 h-1"
          ></UiBadge>

          Bill Payments
        </li>
        <li class="flex items-center gap-4">
          <UiBadge class="rounded-full bg-[#CDA352] w-2 mx-2 p-1 h-1"></UiBadge>

          Pos Transaction
        </li>
        <li class="flex items-center gap-4">
          <UiBadge class="rounded-full bg-[#F1E5AC] w-2 mx-2 p-1 h-1"></UiBadge>

          ATM Withdrawal
        </li>
      </ul>
    </div>
  </UiCard>
</template>
