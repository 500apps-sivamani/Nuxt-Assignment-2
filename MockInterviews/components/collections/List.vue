<template>
  <div class="px-4 sm:px-6 lg:px-8 p-5">
    <div class="sm:flex sm:items-center">
      <div class="sm:flex-auto">
        <h1 class="text-base font-semibold leading-6 text-gray-900">
          Mock Interviews
        </h1>
        <p class="mt-2 text-sm text-gray-700">
          "Opportunities don't happen, you create them."
        </p>
      </div>
      <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
        <button
          @click="AddMockDetails"
          type="button"
          class="block rounded-md bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
        >
          Add Mock Details
        </button>
      </div>
    </div>
    <div class="mt-8 flow-root">
      <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
          <table class="min-w-full divide-y divide-gray-300">
            <thead>
              <tr>
                <th
                  scope="col"
                  class="whitespace-nowrap py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-0"
                >
                  Candidate Name
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Type
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Max Time Allowed
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Due Date
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Difficulty Level
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Description
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Questions
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Instructions
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Multile Attempts Allowed
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Status
                </th>
                <th
                  scope="col"
                  class="relative whitespace-nowrap py-3.5 pl-3 pr-4 sm:pr-0"
                >
                  Last Modified Date
                </th>
              </tr>
            </thead>
            <tbody class="divide-y divide-gray-200 bg-white">
              <tr v-for="candidate in getTemplateData" :key="candidate">
                <td
                  class="whitespace-nowrap py-2 pl-4 pr-3 text-sm text-gray-500 sm:pl-0"
                >
                  {{ candidate.name }}
                </td>
                <td
                  class="whitespace-nowrap px-2 py-2 text-sm font-medium text-gray-900"
                >
                  {{ candidate.type }}
                </td>
                <td
                  class="whitespace-nowrap px-2 py-2 text-center text-sm text-gray-900"
                >
                  {{ candidate.max_time_allowed }}
                </td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">
                  {{ candidate.due_date }}
                </td>
                <td
                  class="whitespace-nowrap px-2 text-center py-2 text-sm text-gray-500"
                >
                  {{ candidate.difficulty_level }}
                </td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">
                  {{ candidate.description }}
                </td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">
                  {{ candidate.questions }}
                </td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">
                  {{ candidate.instructions }}
                </td>
                <td
                  class="whitespace-nowrap px-2 text-center py-2 text-sm text-gray-500"
                >
                  {{ candidate.multiple_attempts_allowed }}
                </td>

                <td
                  class="whitespace-nowrap px-2 py-2 text-center text-sm text-gray-500"
                >
                  {{ candidate.status }}
                </td>
                <td
                  class="whitespace-nowrap px-2 py-2 text-center text-sm text-gray-500"
                >
                  {{ candidate.last_modified_date }}
                </td>
                <td
                  class="relative whitespace-nowrap py-2 pl-3 pr-4 text-right text-sm font-medium sm:pr-0"
                ></td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from "vue";

const props = defineProps({
  getTemplateData: {
    type: Array,
  },
});
const emit = defineEmits(["is_sidebar"]);

//open sidebar for Add
const AddMockDetails = () => {
  emit("is_sidebar");
};
</script>
