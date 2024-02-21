<script lang="ts" setup>
import { useForm } from "vee-validate";
import {
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { customerLoginFormSchema } from "~/validations/customerLoginFormSchema";

const isLoading = ref(false);

const form = useForm({
  validationSchema: customerLoginFormSchema,
});

const onSubmit = form.handleSubmit(async (values: any) => {
  isLoading.value = true;

  const { body }: any = await $fetch("/api/login", {
    method: "post",
    body: values,
  }).catch((err) => {
    console.log(err);
    isLoading.value = false;
  });
  // store.email = body.email;
  // setTimeout(() => {
  isLoading.value = false;
  navigateTo("/");
  // }, 3000);
});
</script>

<template>
  <UiCard class="col-span-1 md:p-8 p-6 space-y-6 w-full md:w-2/3">
    <h1 class="font-semibold text-xl">Quick Transfer</h1>
    <form @submit="onSubmit">
      <div class="grid gap-6">
        <FormField v-slot="{ componentField }" name="email">
          <FormItem>
            <FormLabel> Account No.</FormLabel>
            <FormControl>
              <UiInput
                type="text"
                class="h-10"
                placeholder="100012345678"
                v-bind="componentField"
                :disabled="isLoading"
              />
            </FormControl>
            <FormMessage />
          </FormItem>
        </FormField>

        <div class="w-full flex justify-between gap-4">
          <UiButton
            class="hover:bg-fuchsia-700 text-base font-medium w-full"
            :disabled="isLoading"
          >
            <Icon
              name="svg-spinners:8-dots-rotate"
              v-if="isLoading"
              class="mr-2 h-4 w-4 animate-spin"
            ></Icon>

            Transfer
          </UiButton>
          <UiButton
            class="hover:bg-accent hover:opacity-70 bg-accent text-base font-medium w-full"
            :disabled="isLoading"
          >
            <Icon
              name="svg-spinners:8-dots-rotate"
              v-if="isLoading"
              class="mr-2 h-4 w-4 animate-spin"
            ></Icon>

            Save for later
          </UiButton>
        </div>
      </div>
    </form>
  </UiCard>
</template>
