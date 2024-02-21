<script setup lang="ts">
import { ref } from "vue";
import { cn } from "@/lib/utils";
// import { useForm } from "vee-validate";
import {
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { customerLoginFormSchema } from "~/validations/customerLoginFormSchema";
import { useForm } from "vee-validate";
import { Icons } from "../icons";
const store = useAuthStore();

const isLoading = ref(false);

const form = useForm();
let showPassword = ref(false);

const togglePasswordVisibility = () => {
  showPassword.value = !showPassword.value;
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
  navigateTo("/accounts");
  // }, 3000);
});
</script>

<template>
  <div :class="cn('grid gap-6', $attrs.class ?? '')">
    <form @submit="onSubmit">
      <div class="grid gap-6">
        <FormField v-slot="{ componentField }" name="email">
          <FormItem>
            <FormLabel> User ID</FormLabel>
            <FormControl>
              <UiInput
                type="email"
                placeholder="name@example.com"
                v-bind="componentField"
                :disabled="isLoading"
              />
            </FormControl>
            <FormMessage />
          </FormItem>
        </FormField>

        <FormField v-slot="{ componentField }" name="password">
          <FormItem>
            <FormLabel>Password</FormLabel>
            <FormControl>
              <div
                className="relative flex items-center bg-input rounded-lg pl- focus-within:ring-1 focus-within:ring-primary"
              >
                <UiInput
                  :type="[showPassword ? 'text' : 'password']"
                  placeholder="******"
                  v-bind="componentField"
                  :disabled="isLoading"
                />

                <Icons.hide
                  v-if="showPassword"
                  class="absolute flex right-0 pr-3 items-center w-8 h-8"
                  @Click="togglePasswordVisibility"
                />

                <Icons.view
                  v-else
                  class="absolute flex right-0 pr-3 items-center w-8 h-8"
                  @Click="togglePasswordVisibility"
                />
              </div>
            </FormControl>
            <FormMessage />
          </FormItem>
        </FormField>

        <FormField v-slot="{ componentField }" name="otp">
          <FormItem>
            <FormLabel>OTP</FormLabel>
            <FormControl>
              <UiInput
                type="text"
                placeholder="1234"
                v-bind="componentField"
                :disabled="isLoading"
              />
            </FormControl>
            <FormMessage />
          </FormItem>
        </FormField>

        <UiButton class="hover:bg-fuchsia-700 text-lg" :disabled="isLoading">
          <Icon
            name="svg-spinners:8-dots-rotate"
            v-if="isLoading"
            class="mr-2 h-4 w-4 animate-spin"
          ></Icon>

          Login
        </UiButton>
      </div>
    </form>
  </div>
</template>
