<script setup lang="ts">
import { ref } from "vue";
import Button from "@/components/ui/button.vue";

const message = ref("Hello World!");
</script>

<template>
  <div
    class="min-h-screen bg-background flex flex-col items-center justify-center p-4"
  >
    <div class="w-full max-w-md p-6 bg-card rounded-lg shadow-lg">
      <h1 class="text-2xl font-bold text-center text-primary mb-4">
        {{ message }}
      </h1>
      <p class="text-center text-muted-foreground">Welcome to our ERP system</p>
      <div class="w-full max-w-md space-y-4">
        <Button>Click me</Button>
        <Button variant="secondary">Secondary</Button>
        <Button variant="outline">Outline</Button>
      </div>
    </div>
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
