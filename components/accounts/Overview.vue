<script setup lang="ts">
import { VisArea, VisAxis, VisStackedBar, VisXYContainer } from "@unovis/vue";
import { Icons } from "../icons";

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
const y = (d: DataRecord) =>
  typeof d.total === "string" ? parseInt(d.total.replace(/\D/g, "")) : d.total;

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
  <UiCard class="p-6 space-y-8 w-full">
    <div
      class="flex flex-col md:flex-row items-start md:items-center gap-4 md:gap-8"
    >
      <h1 class="font-semibold text-xl mr-auto">Transaction Flow</h1>
      <UiSelect default-value="Debit">
        <UiSelectTrigger class="md:w-fit">
          <div class="flex gap-2">
            <Icons.calender />
            <UiSelectValue placeholder="Transactions" />
          </div>
        </UiSelectTrigger>
        <UiSelectContent>
          <UiSelectGroup>
            <UiSelectItem value="Debit"> Debit </UiSelectItem>
            <UiSelectItem value="Withdrawal"> Withdrawal </UiSelectItem>
          </UiSelectGroup>
        </UiSelectContent>
      </UiSelect>

      <UiSelect default-value="6">
        <UiSelectTrigger class="md:w-fit">
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
            <UiSelectItem value="1"> Monthly </UiSelectItem>
          </UiSelectGroup>
        </UiSelectContent>
      </UiSelect>
    </div>

    <VisXYContainer
      height="350px"
      :margin="{ left: 20, right: 20 }"
      :data="data"
    >
      <VisArea :x="x" :y="y" color="#E4CA86" :rounded-corners="4" />
      <VisAxis
        type="x"
        :num-ticks="data.length"
        :tick-format="(index: number) => data[index]?.name"
        :grid-line="false"
        :tick-line="true"
        color="#888888"
      />
      <VisAxis
        type="y"
        :num-ticks="data.length"
        :tick-format="(index: number) => data[index]?.name"
        :grid-line="false"
        :tick-line="false"
        :domain-line="false"
        color="#888888"
      />
    </VisXYContainer>
  </UiCard>
</template>
