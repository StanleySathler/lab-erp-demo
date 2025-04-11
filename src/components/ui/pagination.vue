<script setup lang="ts">
import { cn } from "@/lib/utils";
import Button from "./button.vue";

const props = defineProps<{
  currentPage: number;
  totalPages: number;
  onPageChange: (page: number) => void;
}>();
</script>

<template>
  <div class="flex items-center justify-center space-x-2 py-4">
    <Button
      variant="outline"
      size="sm"
      :disabled="currentPage === 1"
      @click="onPageChange(currentPage - 1)"
    >
      Previous
    </Button>
    <div class="flex items-center space-x-2">
      <Button
        v-for="page in totalPages"
        :key="page"
        variant="outline"
        size="sm"
        :class="
          cn(
            'w-8 h-8 p-0',
            currentPage === page && 'bg-primary text-primary-foreground'
          )
        "
        @click="onPageChange(page)"
      >
        {{ page }}
      </Button>
    </div>
    <Button
      variant="outline"
      size="sm"
      :disabled="currentPage === totalPages"
      @click="onPageChange(currentPage + 1)"
    >
      Next
    </Button>
  </div>
</template>
