<script setup lang="ts">
import Table from "@/components/ui/table.vue";

// Mocked customer data
const customers = [
  { id: 1, name: "John Doe", email: "john@example.com" },
  { id: 2, name: "Jane Smith", email: "jane@example.com" },
  { id: 3, name: "Bob Johnson", email: "bob@example.com" },
  { id: 4, name: "Alice Brown", email: "alice@example.com" },
  { id: 5, name: "Charlie Wilson", email: "charlie@example.com" },
  { id: 6, name: "Diana Miller", email: "diana@example.com" },
  { id: 7, name: "Edward Davis", email: "edward@example.com" },
  { id: 8, name: "Fiona Garcia", email: "fiona@example.com" },
  { id: 9, name: "George Martinez", email: "george@example.com" },
  { id: 10, name: "Helen Taylor", email: "helen@example.com" },
];
</script>

<template>
  <div class="container mx-auto py-10">
    <div class="flex flex-col gap-4">
      <h1 class="text-3xl font-bold">Customers</h1>
      <div class="rounded-md border">
        <Table>
          <thead>
            <tr class="border-b transition-colors hover:bg-muted/50">
              <th class="h-12 px-4 text-left align-middle font-medium">ID</th>
              <th class="h-12 px-4 text-left align-middle font-medium">Name</th>
              <th class="h-12 px-4 text-left align-middle font-medium">
                Email
              </th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="customer in customers"
              :key="customer.id"
              class="border-b transition-colors hover:bg-muted/50"
            >
              <td class="p-4 align-middle">{{ customer.id }}</td>
              <td class="p-4 align-middle">{{ customer.name }}</td>
              <td class="p-4 align-middle">{{ customer.email }}</td>
            </tr>
          </tbody>
        </Table>
      </div>
    </div>
  </div>
</template>
