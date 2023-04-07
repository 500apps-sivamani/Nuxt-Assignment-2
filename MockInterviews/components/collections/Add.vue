<template>
  <div>
    <TransitionRoot as="template" :show="open">
      <Dialog as="div" class="relative z-10" @close="open = false">
        <div class="fixed inset-0" />

        <div class="fixed inset-0 overflow-hidden">
          <div class="absolute inset-0 overflow-hidden">
            <div
              class="pointer-events-none fixed inset-y-0 right-0 flex max-w-full pl-10 sm:pl-16"
            >
              <TransitionChild
                as="template"
                enter="transform transition ease-in-out duration-500 sm:duration-700"
                enter-from="translate-x-full"
                enter-to="translate-x-0"
                leave="transform transition ease-in-out duration-500 sm:duration-700"
                leave-from="translate-x-0"
                leave-to="translate-x-full"
              >
                <DialogPanel class="pointer-events-auto w-screen max-w-2xl">
                  <div
                    class="flex h-full flex-col overflow-y-scroll bg-white py-6 shadow-xl"
                  >
                    <div class="px-4 sm:px-6">
                      <div class="items-start justify-between">
                        <DialogTitle
                          class="text-base font-semibold leading-6 text-white-900 mb-5"
                          >Add Candidates</DialogTitle
                        >
                        <hr />

                        <div class="mt-6 py-6">
                          <label />Candidate Name
                          <input
                            v-model="candidateName"
                            type="text"
                            class="block mb-3 px-3 rounded-md border-0 py-2 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 w-[100%]"
                          />
                          <label for="test-type">Test Type</label>
                          <select
                            v-model="testType"
                            id="test-type"
                            class="block mb-3 px-3 rounded-md border-0 py-2 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 w-[100%]"
                          >
                            <option value="practice">Practice</option>
                            <option value="videoProfiles">
                              Video Profiles
                            </option>
                          </select>

                          <label />Max Time
                          <input
                            v-model="maxTime"
                            type="number"
                            class="block mb-3 px-3 rounded-md border-0 py-2 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 w-[100%]"
                          />
                          <label />Due Date
                          <input
                            v-model="dueDate"
                            type="datetime-local"
                            class="block mb-3 px-3 rounded-md border-0 py-2 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 w-[100%]"
                          />
                          <label />Difficulty Level
                          <select
                            v-model="level"
                            id="level-type"
                            class="block mb-3 px-3 rounded-md border-0 py-2 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 w-[100%]"
                          >
                            <option value="Easy">Easy</option>
                            <option value="Hard">Hard</option>
                            <option value="Medium">Hard</option>
                          </select>
                          <label />Description
                          <textarea
                            v-model="description"
                            type="text"
                            class="p-4 block w-full rounded-md border-0 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:py-1.5 sm:text-sm sm:leading-6"
                          />
                          <label />Questions
                          <input
                            v-model="questions"
                            type="select"
                            class="block mb-3 px-3 rounded-md border-0 py-2 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 w-[100%]"
                          />
                          <label />No.of Attempts
                          <input
                            v-model="attempts"
                            type="number"
                            class="block mb-3 px-3 rounded-md border-0 py-2 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 w-[100%]"
                          />
                          <label />Instructions
                          <input
                            v-model="instructions"
                            type="select"
                            class="block mb-3 px-3 rounded-md border-0 py-2 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 w-[100%]"
                          />
                          <label />Status
                          <input
                            v-model="status"
                            type="number"
                            id="level-type"
                            class="block mb-3 px-3 rounded-md border-0 py-2 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 w-[100%]"
                          />
                          <label />Last Modified Date
                          <input
                            v-model="modifieData"
                            type="datetime-local"
                            class="block mb-3 px-3 rounded-md border-0 py-2 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 w-[100%]"
                          />
                        </div>

                        <div class="ml-3 flex h-7 items-center">
                          <button
                            type="button"
                            class="rounded-md bg-white text-gray-400 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
                            @click="open = false"
                          >
                            <span class="sr-only">Close panel</span>
                          </button>
                        </div>
                      </div>
                    </div>
                    <div class="relative flex-1 px-2 sm:px-6">
                      <!-- Your content -->
                      <div class="bg-gray h-auto">
                        <div class="bg-gray-50 mx-auto px-4 py-3">
                          <div class="text-center mb-0 rounded-0">
                            <div class="flex justify-end mr-3 mt-4">
                              <button
                                @click="open = false"
                                type="button"
                                class="border rounded-md bg-white py-2 px-3 text-sm font-semibold text-gray-600 shadow-sm hover:bg-gray-50 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 mr-3"
                              >
                                Cancel
                              </button>
                              <button
                                type="button"
                                class="rounded-md bg-indigo-600 py-2 px-4 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                                @click="postData()"
                              >
                                Save
                              </button>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </DialogPanel>
              </TransitionChild>
            </div>
          </div>
        </div>
      </Dialog>
    </TransitionRoot>
  </div>
</template>
<script setup lang="ts">
import { ref, defineEmits } from "vue";

import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";

const emit = defineEmits(["postDatabody"]);

let candidateName = ref("");
let testType = ref("");
let maxTime = ref();
let dueDate = ref("");
let level = ref("");
let description = ref("");
let questions = ref([]);
let attempts = ref();
let instructions = ref([]);
let status = ref();
let modifieData = ref("");

const open = ref(true);

//sending body to the emit
const postData = async () => {
  let body = {
    name: candidateName.value,
    type: "practice",
    max_time_allowed: maxTime.value,
    due_date: "2023-04-07T04:56:07.759Z",
    difficulty_level: "Easy",
    description: description.value,
    questions: {},
    multiple_attempts_allowed: attempts.value,
    instructions: {},
    status: status.value,
    last_modified_date: "2023-04-07T04:56:07.759Z",
  };
  emit("postDatabody", body);
};
</script>
