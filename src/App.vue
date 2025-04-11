<script setup lang="ts">
import { ref } from "vue";
import Button from "@/components/ui/button.vue";
import Customers from "@/pages/Customers.vue";

const currentPage = ref("home");
</script>

<template>
  <div class="min-h-screen bg-background">
    <nav class="border-b">
      <div class="container mx-auto flex h-16 items-center px-4">
        <div class="flex gap-4">
          <Button
            variant="ghost"
            :class="currentPage === 'home' ? 'bg-muted' : ''"
            @click="currentPage = 'home'"
          >
            Home
          </Button>
          <Button
            variant="ghost"
            :class="currentPage === 'customers' ? 'bg-muted' : ''"
            @click="currentPage = 'customers'"
          >
            Customers
          </Button>
        </div>
      </div>
    </nav>

    <main class="container mx-auto">
      <div
        v-if="currentPage === 'home'"
        class="flex flex-col items-center justify-center p-4"
      >
        <div class="w-full max-w-md space-y-4">
          <Button>Click me</Button>
          <Button variant="secondary">Secondary</Button>
          <Button variant="outline">Outline</Button>
        </div>
      </div>
      <Customers v-else />
    </main>
  </div>
</template>

<style scoped>
/* Responsive design adjustments */
@media (max-width: 640px) {
  .max-w-md {
    max-width: 100%;
  }
}
</style>
