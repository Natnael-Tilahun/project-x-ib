<script setup lang="ts">
import { format } from "date-fns";
import { ref, onMounted } from "vue";
import { cn } from "~/lib/utils";
import { Calendar as CalendarIcon } from "lucide-vue-next";
import { Icons } from "~/components/icons";
import { jsPDF } from "jspdf";

definePageMeta({
  layout: "auth-layout",
});

interface AccountData {
  availableBalance: string;
  id: string;
  accountId: string; // Add this line
  productId: string;
  accountName: string;
  currencyCode: string;
  accountCurrency: string;
  accountHolder: string;
  name: string;
  isBusinessAccount: number;
  showTransactions: number;
  currentBalance: string;
  interestRate: number;
  availableCredit: number;
  principalBalance: string;
  internalAccount?: string;
  email: string;
  phone: string;
  transactions: Transaction[];
}

interface Transaction {
  description: string;
  notes: string;
  id: string;
  customerId: string;
  expenseCategoryId: string;
  typeId: string;
  referenceId: string;
  fromAccountNumber: string;
  fromAccountBalance: string;
  toAccountNumber: string;
  toAccountBalance: string;
  depositAmount?: number;
  withdrawalAmount?: number;
  transactionDate: string;
  transactionCurrency: string;
  serviceCharge: string;
  details: string;
  txnType: string;
}

const startDate = ref<Date>();
const endDate = ref<Date>();
const account = ref<string>();
const data = ref<AccountData[]>([]);

async function getData(): Promise<AccountData[]> {
  // Fetch data from your API here.
  return [
    {
      availableBalance: "90000",
      id: "adfads3432sddf34",
      accountId: "1000179835599",
      productId: "saving",
      accountName: "Natnael Tilahun",
      currencyCode: "Birr",
      accountCurrency: "ETB",
      accountHolder: "Natnael Tilahun",
      name: "Natnael Tilahun",
      isBusinessAccount: 0,
      showTransactions: 1,
      currentBalance: "30000",
      interestRate: 7,
      availableCredit: 20000,
      principalBalance: "30000",
      email: "natnaeltilahun97@gmail.com",
      phone: "0933654654",
      transactions: [
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
          details: "Transfer from Telebirr",
          txnType: "Mobile Money Txn",
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
          details: "Transfer from Telebirr",
          txnType: "Mobile Money Txn",
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
          details: "Transfer from Telebirr",
          txnType: "Mobile Money Txn",
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
          amount: 1000,
          transactionDate: "Apr 20,2023",
          transactionCurrency: "Birr",
          serviceCharge: "10",
          details: "Transfer from Telebirr",
          txnType: "Mobile Money Txn",
        },
      ],
    },
    {
      availableBalance: "70000",
      id: "adfads3432sddf34",
      accountId: "1000122222222",
      productId: "saving",
      accountName: "Kalabe Halefom",
      currencyCode: "Birr",
      accountCurrency: "ETB",
      accountHolder: "Natnael Tilahun",
      name: "Natnael Tilahun",
      isBusinessAccount: 0,
      showTransactions: 1,
      currentBalance: "50000",
      interestRate: 7,
      availableCredit: 20000,
      principalBalance: "30000",
      email: "kalabehalefom@gmail.com",
      phone: "0933654654",
      transactions: [
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
          amount: 20000,
          transactionDate: "Apr 1,2023",
          transactionCurrency: "Birr",
          serviceCharge: "10",
          details: "Transfer from Telebirr",
          txnType: "Mobile Money Txn",
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
          amount: 5000,
          transactionDate: "Apr 2,2023",
          transactionCurrency: "Birr",
          serviceCharge: "10",
          details: "Transfer from Telebirr",
          txnType: "Mobile Money Txn",
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
          amount: 10000,
          transactionDate: "Apr 14,2023",
          transactionCurrency: "Birr",
          serviceCharge: "10",
          details: "Transfer from Telebirr",
          txnType: "Mobile Money Txn",
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
          amount: 3000,
          transactionDate: "Apr 20,2023",
          transactionCurrency: "Birr",
          serviceCharge: "10",
          details: "Transfer from Telebirr",
          txnType: "Mobile Money Txn",
        },
      ],
    },
    {
      availableBalance: "100000",
      id: "adfads3432sddf34",
      accountId: "1000133333333",
      productId: "Saving",
      accountName: "Yohannes Seifu",
      currencyCode: "Birr",
      accountCurrency: "ETB",
      accountHolder: "Natnael Tilahun",
      name: "Natnael Tilahun",
      isBusinessAccount: 0,
      showTransactions: 1,
      currentBalance: "50000",
      interestRate: 7,
      availableCredit: 80000,
      principalBalance: "30000",
      internalAccount: "<string>",
      email: "natnaeltilahun97@gmail.com",
      phone: "0933654654",
      transactions: [
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
          amount: 60000,
          transactionDate: "Apr 12,2023",
          transactionCurrency: "Birr",
          serviceCharge: "10",
          details: "Transfer from Telebirr",
          txnType: "Mobile Money Txn",
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
          amount: 5000,
          transactionDate: "Apr 12,2023",
          transactionCurrency: "Birr",
          serviceCharge: "10",
          details: "Transfer from Telebirr",
          txnType: "Mobile Money Txn",
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
          amount: 10000,
          transactionDate: "Apr 14,2023",
          transactionCurrency: "Birr",
          serviceCharge: "10",
          details: "Transfer from Telebirr",
          txnType: "Mobile Money Txn",
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
          amount: 20000,
          transactionDate: "Apr 20,2023",
          transactionCurrency: "Birr",
          serviceCharge: "10",
          details: "Transfer from Telebirr",
          txnType: "Mobile Money Txn",
        },
      ],
    },
  ];
}

onMounted(async () => {
  data.value = await getData();
  account.value = data.value[0]?.accountId;
});

const selectedAccount = computed(() => {
  return data.value.find((item) => item?.accountId === account.value);
});

const filteredTransactions = computed(() => {
  if (selectedAccount.value) {
    return selectedAccount.value?.transactions || [];
  }
  return [];
});

function printFacture() {
  let component: HTMLElement = <HTMLElement>document.getElementById("facture");

  let componentWidth = component.offsetWidth;
  let screenHeight = window.screen.height;
  let doc = new jsPDF({
    orientation: "landscape",
    unit: "px",
    format: [componentWidth, screenHeight],
    compress: true,
  });
  // let component: HTMLElement = <HTMLElement>document.getElementById("facture");
  doc.html(component, {
    margin: [10, 0, 50, 0],
    callback: function (doc) {
      doc.save(`Account Statement.pdf`);
    },
    x: 0,
    y: 0,
    autoPaging: "text",
  });
}
</script>

<template>
  <div class="w-full p-8 h-full space-y-6">
    <UiSelect v-model="account">
      <UiSelectTrigger class="w-1/3 h-14 rounded-xl">
        <UiSelectValue class="text-slate-400" placeholder="Select account" />
      </UiSelectTrigger>
      <UiSelectContent>
        <UiSelectGroup>
          <UiSelectItem
            v-for="item in data"
            :key="item.id"
            :value="item.accountId"
          >
            {{ item.accountId }}
          </UiSelectItem>
        </UiSelectGroup>
      </UiSelectContent>
    </UiSelect>
    <div class="space-y-8">
      <div class="space-y-2">
        <h1 class="text-foreground text-base font-normal">
          Select Statement Duration
        </h1>
        <div class="flex gap-24 items-center">
          <UiPopover>
            <UiPopoverTrigger as-child>
              <UiButton
                :variant="'outline'"
                :class="
                  cn(
                    'w-fit rounded-lg justify-start text-left font-medium text-base',
                    !startDate && 'text-secondary-foreground'
                  )
                "
              >
                <CalendarIcon class="mr-2 h-4 w-4" />
                <span>{{
                  startDate ? format(startDate, "PPP") : "DD/MM/YYYY"
                }}</span>
                <Icons.arrowDown class="ml-4 h-4 w-4" />
              </UiButton>
            </UiPopoverTrigger>
            <UiPopoverContent class="w-auto p-0">
              <UiCalendar v-model="startDate" />
            </UiPopoverContent>
          </UiPopover>
          <UiPopover>
            <UiPopoverTrigger as-child>
              <UiButton
                :variant="'outline'"
                :class="
                  cn(
                    'w-fit rounded-lg justify-start text-left font-medium text-base mr-auto',
                    !endDate && 'text-secondary-foreground'
                  )
                "
              >
                <CalendarIcon class="mr-2 h-4 w-4" />
                <span>{{
                  endDate ? format(endDate, "PPP") : "DD/MM/YYYY"
                }}</span>
                <Icons.arrowDown class="ml-4 h-4 w-4" />
              </UiButton>
            </UiPopoverTrigger>
            <UiPopoverContent class="w-auto p-0">
              <UiCalendar v-model="endDate" />
            </UiPopoverContent>
          </UiPopover>
          <UiButton class="px-8" @click="printFacture"
            >Print
            <Icons.print class="ml-4 h-4 w-4" />
          </UiButton>
        </div>
      </div>

      <!-- Account Statement -->
      <div
        id="facture"
        class="bg-[#FCFCFC] w-full py-4 px-7 print:bg-green-500"
      >
        <div class="flex justify-between">
          <img src="/cbe-logo.png" class="w-64 h-fit" alt="Logo" />
          <div class="space-y-2">
            <h1 class="text-2xl">Account Statement</h1>
            <div class="flex items-center text-accent gap-4 tracking-wider">
              <p class="">
                From :
                {{ startDate ? startDate?.toLocaleDateString() : "DD/MM/YYYY" }}
              </p>
              <p class="">
                To:
                {{ startDate ? endDate?.toLocaleDateString() : "DD/MM/YYYY" }}
              </p>
            </div>
          </div>
          <p>Date: {{ new Date().toLocaleDateString() }}</p>
        </div>

        <div class="space-y-2 px-12 py-6 lg:w-1/3 md:w-1/2 w-full max-w-full">
          <div class="grid grid-cols-2 w-full gap-4">
            <p class="font-bold">Account Holder Name:</p>
            <p>{{ selectedAccount?.accountName }}</p>
          </div>
          <div class="grid grid-cols-2 w-full gap-4">
            <p class="font-bold">Account Number:</p>
            <p>{{ selectedAccount?.accountId }}</p>
          </div>
          <div class="grid grid-cols-2 w-full gap-4">
            <p class="font-bold">Account Type:</p>
            <p>{{ selectedAccount?.productId }}</p>
          </div>
          <div class="grid grid-cols-2 w-full gap-4">
            <p class="font-bold">Account Currency:</p>
            <p>{{ selectedAccount?.accountCurrency }}</p>
          </div>
        </div>

        <UiTable class="border-t-[1px]">
          <UiTableHeader>
            <UiTableRow>
              <UiTableHead class="w-[100px]"> # </UiTableHead>
              <UiTableHead class="uppercase font-semibold text-sm"
                >Transaction ID</UiTableHead
              >
              <UiTableHead class="uppercase font-semibold text-sm"
                >Details</UiTableHead
              >
              <UiTableHead class="text-right uppercase font-semibold text-sm">
                TXN Type
              </UiTableHead>
              <UiTableHead class="text-right uppercase font-semibold text-sm">
                Amount
              </UiTableHead>
              <UiTableHead class="text-right uppercase font-semibold text-sm">
                Date
              </UiTableHead>
            </UiTableRow>
          </UiTableHeader>
          <UiTableBody>
            <UiTableRow
              v-for="(transaction, index) in filteredTransactions"
              :key="index"
            >
              <UiTableCell class="font-medium"> {{ index }} </UiTableCell>
              <UiTableCell class="font-medium text-sm uppercase">
                <div>
                  <p class="">{{ transaction.id }}</p>
                  <p
                    v-if="transaction.typeId == 'Deposit'"
                    class="text-xs text-[#2DD683] capitalize"
                  >
                    {{ transaction.typeId }}
                  </p>
                  <p
                    v-if="transaction.typeId == 'Withdrawal'"
                    class="text-xs text-[#E74A51] capitalize"
                  >
                    {{ transaction.typeId }}
                  </p>
                </div>
              </UiTableCell>
              <UiTableCell>{{ transaction.details }}</UiTableCell>
              <UiTableCell class="text-right">
                {{ transaction.txnType }}
              </UiTableCell>
              <UiTableCell class="text-right">
                <p
                  v-if="transaction.typeId == 'Deposit'"
                  class="text-[#2DD683]"
                >
                  + {{ transaction.amount }}
                </p>

                <p
                  v-if="transaction.typeId == 'Withdrawal'"
                  class="text-[#E74A51]"
                >
                  - {{ transaction.amount }}
                </p>
              </UiTableCell>
              <UiTableCell class="text-right">
                {{ transaction.transactionDate }}
              </UiTableCell>
            </UiTableRow>
          </UiTableBody>
        </UiTable>
      </div>
      <!-- End of Account Statement -->
    </div>
  </div>
</template>

<style lang="postcss" scoped></style>
