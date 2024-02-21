<script lang="ts" setup>
import { watchOnce } from "@vueuse/core";
import { Icons } from "~/components/icons";
import type { CarouselApi } from "@/components/ui/carousel";
import { ref } from "vue";

const accounts = [
  {
    availableBalance: "90000",
    id: "adfads3432sddf34",
    accountId: "1000179835599",
    productId: "saving",
    accountName: "Natnael Tilahun",
    currencyCode: "Birr",
    accountHolder: "Natnael Tilahun",
    name: "Natnael Tilahun",
    isBusinessAccount: 0,
    showTransactions: 1,
    currentBalance: "30000",
    interestRate: 7,
    availableCredit: 20000,
    principalBalance: "30000",
    internalAccount: "<string>",
    email: "natnaeltilahun97@gmail.com",
    phone: "0933654654",
  },
  {
    availableBalance: "70000",
    id: "adfads3432sddf34",
    accountId: "1000122222222",
    productId: "saving",
    accountName: "Natnael Tilahun",
    currencyCode: "Birr",
    accountHolder: "Natnael Tilahun",
    name: "Natnael Tilahun",
    isBusinessAccount: 0,
    showTransactions: 1,
    currentBalance: "10000",
    interestRate: 7,
    availableCredit: 20000,
    principalBalance: "30000",
    internalAccount: "<string>",
    email: "natnaeltilahun97@gmail.com",
    phone: "0933654654",
  },
  {
    availableBalance: "100000",
    id: "adfads3432sddf34",
    accountId: "1000133333333",
    productId: "Youth",
    accountName: "Natnael Tilahun",
    currencyCode: "Birr",
    accountHolder: "Natnael Tilahun",
    name: "Natnael Tilahun",
    isBusinessAccount: 0,
    showTransactions: 1,
    currentBalance: "50000",
    interestRate: 7,
    availableCredit: 20000,
    principalBalance: "30000",
    internalAccount: "<string>",
    email: "natnaeltilahun97@gmail.com",
    phone: "0933654654",
  },
];

const api = ref<CarouselApi>();
const totalCount = ref(accounts.length);
const current = ref(0);
const showFullAccountId = ref(false);
const showFullAvailableBalance = ref(false);
const showFullCurrentBalance = ref(false);

function toggleAccountIdVisibility() {
  showFullAccountId.value = !showFullAccountId.value;
}

function setApi(val: CarouselApi) {
  api.value = val;
}

function formatAccountNumber(accountId: string) {
  if (showFullAccountId.value) {
    return accountId;
  } else {
    const firstFourDigits = accountId.substring(0, 4);
    const lastTwoDigits = accountId.substring(accountId.length - 2);
    const asterisks = "*".repeat(accountId.length - 6);
    return `${firstFourDigits}${asterisks}${lastTwoDigits}`;
  }
}

function toggleAvailableBalanceVisibility(showFullBalance: string) {
  if (showFullBalance == "showFullAvailableBalance") {
    showFullAvailableBalance.value = !showFullAvailableBalance.value;
  } else {
    showFullCurrentBalance.value = !showFullCurrentBalance.value;
  }
}

// Modify formatAvailableBalance to show full available balance or asterisks based on showFullAvailableBalance
function formatAvailableBalance(balance: string, showFullBalance: any) {
  if (showFullBalance) {
    return balance;
  } else {
    return "*".repeat(balance.length);
  }
}

watchOnce(api, (api) => {
  if (!api) return;

  totalCount.value = api.scrollSnapList().length;
  current.value = api.selectedScrollSnap() + 1;

  api.on("select", () => {
    current.value = api.selectedScrollSnap() + 1;
  });
});
</script>

<template>
  <div
    class="w-full col-span-1 h-fit bg-[url('/backgroundMap.png')] bg-center p-8 md:p-0"
  >
    <UiCarousel class="w-full flex" @init-api="setApi">
      <UiCarouselContent>
        <!-- Iterate over accounts array -->
        <UiCarouselItem
          class="md:h-96 flex flex-col md:items-center h-60 justify-center md:p-6"
          v-for="(account, index) in accounts"
          :key="index"
        >
          <div class="md:space-y-16 space-y-10">
            <div class="flex flex-col gap-2 justify-center items-center">
              <h1 class="md:text-2xl text-lg font-semibold text-foreground">
                Selected Account
              </h1>
              <div class="text-center items-center flex gap-4 md:gap-16">
                <h1
                  class="md:text-2xl text-lg text-primary font-semibold tracking-wide"
                >
                  {{ account.productId }} -
                  {{ formatAccountNumber(account.accountId) }}
                  <!-- {{ account.accountId.substring(0, 4) }}***** -->
                </h1>
                <Icons.hide
                  class="md:w-7 md:h-7 w-5 h-5"
                  @click="toggleAccountIdVisibility"
                />
              </div>
            </div>

            <div class="flex w-full gap-4 md:gap-20">
              <div class="md:space-y-1">
                <p class="md:text-base text-sm font-semibold text-accent">
                  Available Balance
                </p>
                <div class="flex items-center gap-4 md:gap-10">
                  <p class="md:text-xl text-base font-semibold">
                    {{
                      formatAvailableBalance(
                        account.availableBalance,
                        showFullAvailableBalance
                      )
                    }}
                    {{ account.currencyCode }}
                  </p>
                  <Icons.hide
                    class="md:w-7 md:h-7 w-5 h-5"
                    @click="
                      toggleAvailableBalanceVisibility(
                        'showFullAvailableBalance'
                      )
                    "
                  />
                </div>
              </div>

              <UiSeparator
                class="w-[2px] h-22 bg-secondary-foreground"
                orientation="vertical"
              />

              <div class="md:space-y-1">
                <p class="md:text-base text-sm font-semibold text-accent">
                  Locked Amount
                </p>
                <div class="flex items-center gap-4 md:gap-10">
                  <p class="md:text-xl text-base font-semibold">
                    {{
                      formatAvailableBalance(
                        account.currentBalance,
                        showFullCurrentBalance
                      )
                    }}
                    {{ account.currencyCode }}
                  </p>
                  <Icons.hide
                    class="md:w-7 md:h-7 w-5 h-5"
                    @click="
                      toggleAvailableBalanceVisibility('showFullCurrentBalance')
                    "
                  />
                </div>
              </div>
            </div>
          </div>
        </UiCarouselItem>
      </UiCarouselContent>
      <UiCarouselPrevious />
      <UiCarouselNext />
    </UiCarousel>

    <div class="py-2 text-center text-sm text-muted-foreground">
      <UiBadge
        v-for="item of totalCount"
        :key="item"
        :class="[current == item ? 'bg-primary' : 'bg-primary opacity-20']"
        class="rounded-full w-2 mx-2 p-1 h-1"
      ></UiBadge>
      <!-- Slide {{ current }} of {{ totalCount }} -->
    </div>
  </div>
</template>

<style lang="postcss" scoped></style>
