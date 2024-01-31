<script setup lang="ts">
import { ref } from "vue";
import { cn } from "@/lib/utils";
import { useForm } from "vee-validate";
import { VueTelInput } from "vue-tel-input";
import "vue-tel-input/vue-tel-input.css";
import countries from "../data/countries.json";

import {
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { customerLoginFormSchema } from "~/validations/customerLoginFormSchema";
const store = useAuthStore();

const isLoading = ref(false);

const phone = ref("");

const form = useForm({
  //   validationSchema: customerLoginFormSchema,
});

const updateSelectedCountry = (country) => {
  phone.value = country.dialCode;
};

const onSubmit = form.handleSubmit(async (values: any) => {
  isLoading.value = true;
  const { body }: any = await $fetch("/api/login", {
    method: "post",
    body: values,
  }).catch((err) => {
    console.log(err);
    isLoading.value = false;
  });
  store.email = body.email;
  // setTimeout(() => {
  isLoading.value = false;
  //   navigateTo("/");
  // }, 3000);
});
</script>

<template>
  <div :class="cn('grid ', $attrs.class ?? '')">
    <form @submit="onSubmit">
      <div class="grid gap-12">
        <vue-tel-input
          class="h-14"
          @country-changed="updateSelectedCountry"
          v-model="phone"
        ></vue-tel-input>
        <!-- {{ countries }} -->
        <UiButton
          size="lg"
          class="hover:bg-fuchsia-700 text-xl h-14"
          :disabled="isLoading"
        >
          <Icon
            name="svg-spinners:8-dots-rotate"
            v-if="isLoading"
            class="mr-2 h-4 w-4 animate-spin"
          ></Icon>

          Sign UP
        </UiButton>
      </div>
    </form>
  </div>
</template>
