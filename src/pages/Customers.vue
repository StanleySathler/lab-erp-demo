<script setup lang="ts">
import { ref, computed } from "vue";
import Table from "@/components/ui/table.vue";
import Button from "@/components/ui/button.vue";
import Pagination from "@/components/ui/pagination.vue";

// Mocked customer data (30 customers)
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
  { id: 11, name: "Ian Anderson", email: "ian@example.com" },
  { id: 12, name: "Julia Clark", email: "julia@example.com" },
  { id: 13, name: "Kevin White", email: "kevin@example.com" },
  { id: 14, name: "Laura Hall", email: "laura@example.com" },
  { id: 15, name: "Michael Lee", email: "michael@example.com" },
  { id: 16, name: "Nancy King", email: "nancy@example.com" },
  { id: 17, name: "Oliver Scott", email: "oliver@example.com" },
  { id: 18, name: "Patricia Green", email: "patricia@example.com" },
  { id: 19, name: "Quentin Adams", email: "quentin@example.com" },
  { id: 20, name: "Rachel Baker", email: "rachel@example.com" },
  { id: 21, name: "Samuel Carter", email: "samuel@example.com" },
  { id: 22, name: "Tina Evans", email: "tina@example.com" },
  { id: 23, name: "Ulysses Foster", email: "ulysses@example.com" },
  { id: 24, name: "Victoria Gray", email: "victoria@example.com" },
  { id: 25, name: "William Hughes", email: "william@example.com" },
  { id: 26, name: "Xena Ingram", email: "xena@example.com" },
  { id: 27, name: "Yvonne Jenkins", email: "yvonne@example.com" },
  { id: 28, name: "Zachary Kelly", email: "zachary@example.com" },
  { id: 29, name: "Amber Lewis", email: "amber@example.com" },
  { id: 30, name: "Brandon Moore", email: "brandon@example.com" },
];

const itemsPerPage = 10;
const currentPage = ref(1);

const totalPages = computed(() => Math.ceil(customers.length / itemsPerPage));

const paginatedCustomers = computed(() => {
  const start = (currentPage.value - 1) * itemsPerPage;
  const end = start + itemsPerPage;
  return customers.slice(start, end);
});

const handlePageChange = (page: number) => {
  currentPage.value = page;
};

const handleAddCustomer = () => {
  // TODO: Implement add customer functionality
  console.log("Add customer clicked");
};

const handleEditCustomer = (customerId: number) => {
  // TODO: Implement edit customer functionality
  console.log("Edit customer:", customerId);
};

const handleDeleteCustomer = (customerId: number) => {
  // TODO: Implement delete customer functionality
  console.log("Delete customer:", customerId);
};
</script>

<template>
  <div class="container mx-auto py-10">
    <div class="flex flex-col gap-4">
      <div class="flex items-center justify-between">
        <h1 class="text-3xl font-bold">Customers</h1>
        <Button @click="handleAddCustomer"> Add Customer </Button>
      </div>
      <div class="rounded-md border">
        <Table>
          <thead>
            <tr class="border-b transition-colors hover:bg-muted/50">
              <th class="h-12 px-4 text-left align-middle font-medium">ID</th>
              <th class="h-12 px-4 text-left align-middle font-medium">Name</th>
              <th class="h-12 px-4 text-left align-middle font-medium">
                Email
              </th>
              <th class="h-12 px-4 text-right align-middle font-medium">
                Actions
              </th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="customer in paginatedCustomers"
              :key="customer.id"
              class="border-b transition-colors hover:bg-muted/50"
            >
              <td class="p-4 align-middle">{{ customer.id }}</td>
              <td class="p-4 align-middle">{{ customer.name }}</td>
              <td class="p-4 align-middle">{{ customer.email }}</td>
              <td class="p-4 align-middle">
                <div class="flex justify-end gap-2">
                  <Button
                    variant="outline"
                    size="sm"
                    @click="handleEditCustomer(customer.id)"
                  >
                    Edit
                  </Button>
                  <Button
                    variant="destructive"
                    size="sm"
                    @click="handleDeleteCustomer(customer.id)"
                  >
                    Delete
                  </Button>
                </div>
              </td>
            </tr>
          </tbody>
        </Table>
        <Pagination
          :current-page="currentPage"
          :total-pages="totalPages"
          @on-page-change="handlePageChange"
        />
      </div>
    </div>
  </div>
</template>
