<script setup lang="ts">
import { ArrowLeft } from "lucide-vue-next";
import { useCarousel } from "./useCarousel";
import type { WithClassAsProps } from "./interface";
import { cn } from "@/lib/utils";
import { Button } from "@/components/ui/button";
import { Icons } from "~/components/icons";

const props = defineProps<WithClassAsProps>();

const { orientation, canScrollPrev, scrollPrev } = useCarousel();
</script>

<template>
  <Button
    :disabled="!canScrollPrev"
    :class="
      cn(
        'touch-manipulation absolute h-8 w-8 border-none  p-0',
        orientation === 'horizontal'
          ? '-left-12 top-1/2 -translate-y-1/2'
          : '-top-12 left-1/2 -translate-x-1/2 rotate-90',
        props.class
      )
    "
    variant="outline"
    @click="scrollPrev"
  >
    <slot>
      <Icons.toLeft class="h-6 w-6 stroke-[6px] hover:fill-accent-foreground" />
    </slot>
  </Button>
</template>
