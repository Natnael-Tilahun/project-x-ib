<script setup lang="ts">
import { ref } from "vue";
import { cn } from "@/lib/utils";
import { useForm } from "vee-validate";
import { VueTelInput } from "vue-tel-input";
import "vue-tel-input/vue-tel-input.css";
// import countries from "../data/countries.json";

import {
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { customerLoginFormSchema } from "~/validations/customerLoginFormSchema";
const store = useAuthStore();

const props = defineProps<{
  handleSuccess: () => void; // Define handleSuccess as a function prop
}>();
const emit: any = undefined; // Define emit as any

const isLoading = ref(false);

const phone = ref("");

const form = useForm({
  //   validationSchema: customerLoginFormSchema,
});

const updateSelectedCountry = (country: any) => {
  phone.value = country.dialCode;
};

const onSubmit = form.handleSubmit(async (values: any) => {
  // isLoading.value = true;
  // const { body }: any = await $fetch("/api/login", {
  //   method: "post",
  //   body: values,
  // }).catch((err) => {
  //   console.log(err);
  //   isLoading.value = false;
  // });
  // Emitting handleSuccess event
  props.handleSuccess();

  // store.email = body.email;
  // setTimeout(() => {
  // isLoading.value = false;
  //   navigateTo("/");
  // }, 3000);
});
</script>

<template>
  <div class="lg:space-y-4 md:space-y-2 w-full">
    <h1
      class="text-2xl md:text-3xl lg:text-4xl uppercase font-medium text-center tracking-wide"
    >
      Sign UP
    </h1>
    <p
      class="lg:text-lg md:text-base text-sm tracking-wide text-secondary-foreground"
    >
      Sign Up to Commercial Bank of Ethiopia Digital Banking platform to elevate
      your banking experience, roviding you with a secure, efficient, and
      user-friendly interface that puts you in control of your finances and
      business.
    </p>
  </div>
  <div class="w-full space-y-4 lg:space-y-6">
    <h3 class="text-base text-foreground">
      Enter Your Mobile Banking Service Activated Phone
    </h3>
    <div :class="cn('grid ', $attrs.class ?? '')">
      <form @submit="onSubmit">
        <div class="grid gap-6 lg:gap-12">
          <vue-tel-input
            class="lg:h-14 md:h-12 h-10"
            @country-changed="updateSelectedCountry"
            v-model="phone"
          ></vue-tel-input>
          <!-- {{ countries }} -->
          <UiButton
            size=""
            class="hover:bg-fuchsia-700 md:text-xl uppercase md:rounded-xl md:h-12 lg:h-14"
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
  </div>
</template>
